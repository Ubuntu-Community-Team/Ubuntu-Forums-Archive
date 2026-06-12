---
title: "cant acess root account on openindiana"
date: 2019-12-17
forum: Any Other OS
---

### Post by wolftrax on 2019-12-17
I installed open indiana on a old laptop just to try it out and created a root account and a user account as usual.  its not been on the internet yet because it cant find the drivers for my wired connection and the wireless just wont connect .  I wrote my passwords down and started getting to know the system and I been able to login to both accounts until last night when I am suddenly denied access to my root account.  

I dont know how to gain access to the system in order to fix it but I know how to do it in ubuntu if I forget passwords but this is not the case here.  its a very simple password and I been able to logn in with it many times so I am sure its not because I forgot or type incorrect passwords. 

the system is fine and I Like it but its also a little buggy.  it wont connect to my wireless and cant find drivers for my wired connection and when I try to shutdown the computer normally it just starts to show a black screen with some random colors flickering on the screen and I have to use sudo poweroff from the commandline to get it to shutdown and turn power off. 

I would like to get the wireless working and install some programs from the repositories and play around with it for a while . I was using open solaris before it got discontinued and I loved that system so I want to see if I can get to be as happy with open indiiana. 

this is why I discovered very quickly my root password must have been changed somehow or there is a bug or whatever is the problem because I need to use the password for configuring the internet and I am sure I use the correct password but it refuses to let me log in . 

anyone knows how to changed password for root account if you forgot ? 

I was hopinig you could just do like in ubuntu and login to a recovery mode shell and change it from there but that did not work either.

---

### Post by TheFu on 2019-12-18
Isn't  openindiana a version of Solaris?  Solaris has been using role-based administration for some time.  root isn't the same.  There are many things that root cannot do based on the role permissions model.  I've never used OpenSolaris, which OpenIndiana is based.

---

### Post by wolftrax on 2019-12-18
yes it seems so.  I found this bugreport [https://www.illumos.org/issues/8203](https://www.illumos.org/issues/8203)  that explains how to get into the terminal as root as well.  
I figured out what the problem was.  

when I create my user I have to make a root password first and then my user account just like in Debian,.  my laptop has two missing keys on the keyboard and some of them are stuck and it wont let me enter any password during installation with my usb keyboard I use .  

when I login the first thing I do is to change the keyboard layout to Danish since it has US keyboard layout even if I selected Danish keyboard layout during installation. 

so I did a little experiment and installed ubuntu with the exact same password I used for the root account password thinking that if one key was stuck or off somehow then I would figure out when I test this on ubuntu. 

the result was similar.  when I open package manager in ubuntu it allows my password to be entered with the USB keyboard but with the terminal using sudo it wont allow it and says its a wrong password then I just use the keyboard on the laptop and it allows me to use sudo when I do that.  

the problem is that when I installed open indiana I knew I had to pick a very simple password since half my keys are dead on the laptop ( I saw something funny on the internet and had my mouth full of beer and then I laughed and mand as result my screen and keyboard got messed up )  so when I changed the password it wont allow me to use it when I use the terminal or try to use sudo if I use the keyboard , but it does not allow me to use it on the wireless settings dialog either. 

so I installed open indiana again and did exactly the same but did not change password and it works fine now.  

open indiana on my old laptop is not a stable system neither is it very useful because the wireless wont connect and the drivers for the wired are missing so I cant use it for internet surfing or install anything that way. 

when I turn off the computer I have to  use sudo poweroff in the terminal or else it just goes the login screen again or goes to a black screen with lots of random white colors flickering .   
however its still worth playing around with but I cant get it to install on any other laptop I own for some reason.   

I don't remember if open solaris had user oles or not.  its years since I used it but I used it a lot surfing the internet but its based on opensolaris or at least replaces opensolaris.  
anyways I figured out what the problem was so I am happy :)

thanks for pointing that out because honestly I forgot that could have something to do with it as well .

---

