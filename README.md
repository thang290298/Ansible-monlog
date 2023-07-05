# ansible-baseline for SmartCloud 2022

Thực hiện duy nhất lần đầu tiên khi cài đặt xong hệ điều hành:

### 1. SmartCloud NTL3 (Colocation)
```
ansible-playbook -i inventory_colo_ntl3.ini config_proxy_colo.yml -e@extra_vars/extra_vars_ntl3.yml

ansible-playbook -i inventory_colo_ntl3.ini playbook.yml -e@extra_vars/extra_vars_ntl3.yml
```

### 2. SmartCloud TT3 (Colocation)
```
ansible-playbook -i inventory_colo_tt3.ini config_proxy_colo.yml -e@extra_vars/extra_vars_tt3.yml

ansible-playbook -i inventory_colo_tt3.ini playbook.yml -e@extra_vars/extra_vars_tt3.yml
```

### 3. SmartCloud NTL4 (ĐHSXKD)
```
ansible-playbook -i inventory_dhsxkd_ntl4.ini playbook.yml -e@extra_vars/extra_vars_ntl4.yml
```

### 4. SmartCloud TT4 (ĐHSXKD)
```
ansible-playbook -i inventory_dhsxkd_tt4.ini playbook.yml -e@extra_vars/extra_vars_tt4.yml
```

### 5. Object Storage (Site NTL4)
```
ansible-playbook -i inventory_obj_ntl4.ini playbook.yml -e@extra_vars/extra_vars_ntl4.yml
```


## Bổ sung thêm máy chủ
```
ansible-playbook -i inventory_dhsxkd_ntl4.ini playbook.yml -e@extra_vars/extra_vars_ntl4.yml --limit kolla-compute03
```
Trong đó:
- `cephssd07-tt4` : tên máy chủ đã được khai báo trong inventory

**Danh sách các role:**
|Role|Mô tả|
|----|-----|
|bonding_network|Cấu hình bonding network|
|setup_baseline|Cài đặt, update các gói cơ bản cho server|
|config_sshd|Cấu hình port, keypair ssh|
|install_ntp|Cấu hình NTP|
|config_cmdlog|Cấu hình cmd log|
|install_docker|Cài đặt, cấu hình docker cho server|