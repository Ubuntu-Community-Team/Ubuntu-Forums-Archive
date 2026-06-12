---
title: "Messed up *.deb files on virtual server"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by SIK70 on 2008-03-03
Hi,

I just got virtual server from my hosting comapny with installed Ubuntu7.04 I installed LAMP and everything went fine. Then because I am a total newbie I got an Idea to Install GUI also and just clicked to install Kubuntu, I didn't realize that it installs awfully lot stuff like amarok and konqueror etc. and the installation got interrupted because disckspace run out :(, stupid me.

Then I couldn't also remove Kubuntu in any smart way because the disk had run out. I ran few commands and delted some files which seemed to be osolote and now all *.deb functions are missing.

Heres some of the commands I used and as you can see nothing works. Is it possible to repair ubuntu installation on virtual server? or how can I atleast install debian functions back?

dpkg -i filename.deb 
Options marked [*] produce a lot of output - pipe it through `less' or `more' !                                       
root@o122:/bin# dpkg -i aptitude.deb                                                                                  
dpkg: error processing aptitude.deb (--install):                                                                      
 cannot access archive: No such file or directory                                                                     
Errors were encountered while processing:                                                                             
 aptitude.deb                                                                                                         
root@o122:/bin# cd ..                                                                                                 
root@o122:/# dpkg -i aptitude.deb                                                                                     
dpkg: error processing aptitude.deb (--install):                                                                      
 cannot access archive: No such file or directory                                                                     
Errors were encountered while processing:                                                                             
 aptitude.deb                                                                                                         
root@o122:/# dpkg -i apt-get.deb                                                                                      
dpkg: error processing apt-get.deb (--install):                                                                       
 cannot access archive: No such file or directory                                                                     
Errors were encountered while processing:                                                                             
 apt-get.deb                                                                                                          
root@o122:/# synaptic                                                                                                 
The program 'synaptic' is currently not installed.  You can install it by typing:                                     
apt-get install synaptic                                                                                              
-bash: synaptic: command not found                                                                                    
root@o122:/# apt-get install apt-get                                                                                  
The program 'apt-get' is currently not installed.  You can install it by typing:                                      
apt-get install apt                                                                                                   
-bash: apt-get: command not found                                                                                     
root@o122:/# apt-get install apt                                                                                      
The program 'apt-get' is currently not installed.  You can install it by typing:                                      
apt-get install apt                                                                                                   
-bash: apt-get: command not found                                                                                     
root@o122:/#

---

### Post by Hospadar on 2008-03-03
are the .deb files actually where you think they are?

Like if you do 
# ls
does it list aptitude.deb and do you have read access to it?

it may be that your stuff is sufficiently messed up that you need a reinstall.

if you can't install stuff with dpkg, and you can't "sudo aptitude" or "sudo apt-get" there really arn't any solutions as easy as a re-install.  also if it's a virtual server they should be able to restore your base image pretty easily.

---

### Post by SIK70 on 2008-03-04
Thanks. It must be the easiest way because I cant find those progs anymore from the place they should be.
So The resetting from image is the easiest and best way. Atleast I now know what full disk in the middle of installation can cause

---

### Post by hyper_ch on 2008-03-04
Can't you just reset the whole virtual server to the state it was delievered to you originally?

Doing that and putting your stuff back online is probably the most-time saving way of doing this.

---

