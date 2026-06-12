---
title: "Installing ATI drivers?"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by MartinAustin on 2005-10-11
Hi everyone --

First time Linux/Ubuntu user, and I must say, I am THOROUGHLY impressed with this distro.  I can't say enough about the ease of use in setting up a wireless network, printing, etc.

I am having some trouble with the typical Linux items though, and it is that I don't understand how to install the following file:  ati-driver-installer-8.16.20-i386.run

When I go to the terminal to execute the file with the following command:

./ati-driver-installer-8.16.20-i386.run

I get the following error:  bash: ./ati-driver-installer-8.16.20-i386.run: Permission denied

Can someone please let me know how I go about doing this?  And can anyone point to an article/tutorial on installation under Linux (RPM, RUN, etc).

Thanks a lot!

I hope to gain knowledge quickly and contribute as much as I can!!!

---

### Post by tacom6 on 2005-10-11
I am a newbie myself. My guess is that you should run this script under ROOT or use SUDO. To allow root account you have to do 'sudo passwd root'. Then before executing the script you would do 'su' ... As for SUDO i don't know much about it since I enabled root account.

By the way, some people don't recommend having root enabled, as for me I don't care. :rolleyes:

---

### Post by Perfect Storm on 2005-10-11
Have you looked at: [http://www.ubuntuforums.org/showthread.php?t=65276](http://www.ubuntuforums.org/showthread.php?t=65276)

---

### Post by MartinAustin on 2005-10-11
I have taken a look at that thread, but without explanation of what the commands are, it's hard to troubleshoot them when they don't work.  Thank you tacom6 for your explanation, I'll give that a shot tonight.

---

### Post by tacom6 on 2005-10-12
Oiii i found this, to become root you can use "sudo su". :rolleyes:

---

### Post by MartinAustin on 2005-10-12
I still get a permission denied error, even after establishing and becoming the root user.  Any other suggestions? :)

---

### Post by Pablo_Escobar on 2005-10-12
Have You tried "chmod +x ati-driver-installer-8.16.20-i386.run"
and then "./ati-driver-installer-8.16.20-i386.run" ?

---

### Post by mlomker on 2005-10-12
> I have taken a look at that thread, but without explanation of what the commands are, it's hard to troubleshoot them when they don't work. 

You could always ask.  If you are running Breezy then it's a lot easier to use the built-in drivers than installing the ATI package.

---

