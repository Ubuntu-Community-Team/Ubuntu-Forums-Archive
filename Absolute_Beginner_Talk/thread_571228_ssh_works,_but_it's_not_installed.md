---
title: "ssh works, but it's not installed?"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by imputerate on 2007-10-09
fellas; this is weird; i've been ssh'ing my brains out from and to my                     
feisty box; and scp'ing, and screen'ing; but                                              
                                                                                          
'dpkg -l ssh', and 'dpkg -l openssh' yield nothing;                                      

and look at this:                                                                         
                                                                                          
root@hodgson-desktop:~# apt-get install -s ssh                                            
Reading package lists... Done                                                             
Building dependency tree                                                                  
Reading state information... Done                                                         
The following packages were automatically installed and are no longer                     
required:                                                                                 
  xaw3dg                                                                                  
Use 'apt-get autoremove' to remove them.                                                  
The following NEW packages will be installed:                                             
  ssh                                                                                     
0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.                           
Inst ssh (1:4.3p2-8ubuntu1 Ubuntu:7.04/feisty)                                            
Conf ssh (1:4.3p2-8ubuntu1 Ubuntu:7.04/feisty)                                            
                                                                                          
what's going on?                                                                          
can i go ahead and "install" ssh?

---

### Post by ofb on 2007-10-09
try,

dpkg -l openssh-client
dpkg -l openssh-server

---

### Post by imputerate on 2007-10-10
that's it; thanks; imputerate

------------------------
try,

dpkg -l openssh-client
dpkg -l openssh-server

---

