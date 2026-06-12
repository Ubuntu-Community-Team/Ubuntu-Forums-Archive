---
title: "Samba - Dependency is not satisfiable: samba - common"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by bereta on 2007-09-15
Hello every one 
I am new to Linux and this is my first taste of it. I just installed ubuntu 6.06 LTS today and i am trying  to share files and folders betwen the ubuntu box and the windows box.

So what i am doing is im going into system>administartion>share folders, and then i get a message saing shareing services not installed, and i check off samba for windows/linux sistems and click apply.It tryes to download the pakage but it comes up with this error:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.22-1ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.22-1ubuntu3.1_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]

So Im thinking that the file has been moved or something and i go to [http://security.ubuntu.com/ubuntu/pool/main/s/samba](http://security.ubuntu.com/ubuntu/pool/main/s/samba) from the web browser and find samba_3.0.22-1ubuntu3.3_i386.deb  among everything else on that page. I download it and when i click to execute the file it gives me in red "Error: Dependency is not Satisfiable: samba-common" 

Can any one help me with this, is there any thing else i need to install or update. i also got this same message for other things i tried to install.

Thanks

---

### Post by louieb on 2007-09-15
Weird problem. Just one question. After you installed Dapper there should have been an orange icon on the upper panel. And a message saying there are updates available. Actually about 180MB of updates if I remember right. Did you install the updates? If not you should.

---

### Post by bereta on 2007-09-15
Thanks for the reply

I dont know what you mean by Dapper, and no i did not get any icons or massages telling me that updates are available.

But shortly after posting went on the upper left to system>administration>update manager and yes it did download about 160-180MB of updates, and that seems to have done it. The updated must have updated the addreses and links because it just pulled samba automaticaly.


Thanks again

---

