---
title: "problem while accessing a share using samba"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by bhavesh on 2006-12-08
Hello people , 
              
1]I am trying to access a share on windows machine using samba .I have installed samba.

2]The share i am trying to access is "//college/docs" , now the machine name college has a fully qualified name "college.ma.us.com". I also have the IP address of the machine.

3] Now when i do “/usr/bin/smbclient –L college.ma.us.com -U username” i can see the various shares accessible from the machine.

4] Can some one tell me how do i go about actually mounting the share on the linux box , i ahve tried "smbmount" , but i dont know how to refer to the machine name , should i be using the 
  a] actual machine name "college"
  b] college.ma.us.com
  c] the ip address of the machine 

which one works with smbmount

Thanks in advance, 
Bhavesh

---

### Post by linuchsan on 2006-12-08
smbmount //college/docs /mount/point -o username=your_user_name password=your_pass

---

