---
title: "Using the playstation move + camera to control your mouse in ubuntu / linux"
date: 2014-08-14
forum: Any Other OS
---

### Post by seefortune on 2014-08-14
I need help connecting my ps3 move to my controler to my laptop running linux mint. 
I would like to use it to controle my mouse. I tried using psMoveInput  and im running into problems left and right but i was able to get the ps  move api installed. Dose anyone know another way to do this without  using PsMoveInput?  
 
incase youre wondering the errors im getting here they are: 
I am on the last step in the installation process in the install.md file. 
When i run it "sudo make install" because it says run as root i get this error and i also tried doing a "make install" 
 
errors: 
 
```
/usr/include/psmoveapi/psmove.h:37:27: fatal error: psmove_config.h: No such file or directory 
 #include "psmove_config.h" 
                           ^ 
compilation terminated. 
make[2]: *** [CMakeFiles/psmoveinput.dir/psmove_handler.cpp.o] Error 1 
make[1]: *** [CMakeFiles/psmoveinput.dir/all] Error 2 
make: *** [all] Error 2
```
 
 
these are some examples:
[HTML]https://www.youtube.com/watch?v=euQU6n1OAqI[/HTML]

the move api:
[HTML]http://thp.io/2010/psmove/[/HTML]

I belive that there should be an easier way to do this install and used like a Gdebi package or somthing.  
I'm also trying to do this on 2 linux based systems :
- lbuntu 
- Linux mint
they are both runing the latest versions as of today 14th August 2014. 
Thanks for any help in advance

---

### Post by howefield on 2014-08-14
Thread moved to "Other Operating Systems and Projects".

---

