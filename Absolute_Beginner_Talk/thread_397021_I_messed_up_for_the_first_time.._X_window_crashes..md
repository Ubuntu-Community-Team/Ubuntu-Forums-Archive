---
title: "I messed up for the first time.. X window crashes."
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-03-30
Yup, this sucks. Im now in windows trying to figure out how to fix Ubuntu.

I used the Synaptic package manager to install the Nvidia GLX driver. Now, I cant remember what exactly I did, but if your reading this in Ubuntu, you can tell me. Theres a command listed in the text describing the Nvidia GLX package, which is like a configuration. I know I used the command, and it told me that it made a backup and that I could revert using another command.

Ugh... I just want to get my X window back up.. Any ideas???

---

### Post by 1/0 on 2007-03-30
Maybe you did one of the following: nvidia-glx-config, nvidia-xconfig

Just reboot in recovery mode and try:

```
sudo dpkg-reconfigure xserver-xorg
```
You'll need to reconfigure xorg. A good thing is to make a paper copy of your existing xorg.conf if you're unsure. 

If that doesn't work maybe remove the nvidia-drivers.

```
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
```

After that reinstall. That's what pops up, from the top of my head.

---

### Post by mikewhatever on 2007-03-30
Boot into Ubuntu. When X fails, you should get to the black screen with an option to log in. Log in and type cd /etc/X11, then type ls and look for a file called xorg.conf.backup or similar. If there, type 
> sudo mv xorg.conf.backup xorg.conf
this should restore the original xorg file, so now type startx.> 

---

### Post by chili555 on 2007-03-30
I assume you can boot Ubuntu to a black screen with a log-in prompt? Log in and do:
```
cd /etc/X11
ls -al | less
```This will allow you to see all the file in the X11 directory and scroll back and forth through them. You are looking for xorg.conf. Notice, you also see creation dates. If you want to restore one to overwrite the faulty one you created, do:```
sudo cp xorg.conf.backup xorg.conf
```Of course, the backup file will have a different name in your system.

Two suggestions: if you do:```
less xorg.conf
```you will see this wording:> # If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorgSo you might try that command to see if the system will help you get back in order.

Second, backups are a wonderful thing. If you are going to muck about with your configuration files, back up the file you are going to play with.```
sud cp <file_u_will_mod> <file_u_will_mod>.0330bak
```I firmly *agree* with mucking about in files. That is one of the true beautiful things about linux, you can bend it to your will and nobody in Redmond or elsewhere can tell you otherwise. You can make a hotrod that out-performs anything commercially available, or you can make a brick. Pop in the install disk and start over, enriched by all that new experience.

---

### Post by GSF1200S on 2007-03-30
Hmmm, none of this stuff worked.

You know, before the whole synaptic package manager I used that program envy. I uninstalled my video drivers and then attempted to reinstall. When the program said my OS wasnt compatible I went to the package manager...

Is there any command I can type in recovery mode that will put my drivers back to where they were when I installed Ubuntu? It worked fine, but I was under the impression I would need to install actual Nvidia drivers for OpenGL acceleration to work... 

I dont know about xorg.conf- I took the persons advice right below my original post and tried to reconfigure it, so did I just eliminate my good copy of xorg.conf? Or does it save multiple backups? I really appreciate the help.. Im living life in windows right now and it sucks-

---

### Post by cowlip on 2007-03-30
sudo dpkg-reconfigure -phigh xserver-xorg

also look through your xorg.conf ('nano -w /etc/X11/xorg.conf') for the 'nvidia' driver.  Try changing it to 'nv' or 'vesa'

---

### Post by GSF1200S on 2007-03-30
> **cowlip said:**
> sudo dpkg-reconfigure -phigh xserver-xorg

also look through your xorg.conf ('nano -w /etc/X11/xorg.conf') for the 'nvidia' driver.  Try changing it to 'nv' or 'vesa'

Yeah, somebody else mentioned this step, and he/she was also right. It WORKED! For some reason I messed up the first time. This forum has not failed me yet, and the trend continues- Thank all of you for the help- seriously! I think every post was accurate, im just a little new to a black screen and a prompt.. windows has taken the smarts out of me....lol!

Looking in Nautilus under the X11 folder, I see the backups for Xorg.conf, but the file system doesnt have a date created. It only has accessed/ modified, so I dont know which is the backup of my original. Id kinda like to go back to my original, but then it seems like this xorg.conf works fine, so maybe I should just leave well enough alone..

Thanks again to all of you!!

---

### Post by cowlip on 2007-03-30
you can find out the created file using a terminal: 'ls -l /etc/X11/'

In Nautilus, I think if you right click on the file, then choose properties, you can get date created.  You may also be able to customize the colums to get date created, in the view menu.

Other file managers, like Thunar, Dolphin (my favorite), or Konqueror should also show the date created normally.

---

