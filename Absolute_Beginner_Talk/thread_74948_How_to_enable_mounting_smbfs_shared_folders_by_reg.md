---
title: "How to enable mounting smbfs shared folders by regular users?"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-13
Hi,

I looked in unofficial ubuntu guide. I tried as mentioned in linux forums to do : 

chmod +s /usr/bin/smbmnt
chmod +s /usr/bin/smbmount

then, I return to the user :

and I tried whatever : mount .... 
and /usr/bin/smbmnt ....

ERROR MESSAGE : NOT ROOT, NO PRIVILEGES
and +s for smbmnt and smbmount
  
(My fstab is correct !, because of root can do : mount //10.x.x.x/user_name )
   
(another question: Btw, how can I share another folder without nautilus)
(cos It's mentioned right click but I HAVE NO SHARE in the right click)
I also tried as said to do : 
gdmflexi --nex (stuff like that)
but not found (I wouldnt like to install it) (I have no internet for the moment)
  
Is there someone In Linux community who could help me ??

tahnk you very much 

I wish & hope that this samba works to use my data on the other PC...

tahnk a lot 

Patrick !!

---

### Post by mlomker on 2005-10-13
>  
(My fstab is correct !, because of root can do : mount //10.x.x.x/user_name )


You can take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=74791") regarding the smb mounting.

---

