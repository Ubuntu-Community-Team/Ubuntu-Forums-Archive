---
title: "Unable to get grub menu to show"
date: 2020-11-02
forum: Apple Hardware Users
---

### Post by williepabon on 2020-11-02
Hi!:

Recently upgraded from Ubuntu 18.04 to 20.04. Everything has been  working OK except that I'm not able to make the grub menu to  appear.  I've tried hitting ESC, SHIFT keys when booting without success. Is there now a new way in Ubuntu 20.04 to make the grub menu to show? Following, the information about my system:

williepabon@williepabon-Macmini:~$ uname -a
Linux williepabon-Macmini 5.4.0-52-generic #57-Ubuntu SMP Thu Oct 15 10:57:00 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
williepabon@williepabon-Macmini:~$
williepabon@williepabon-Macmini:~$ lsb_release -crid
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.1 LTS
Release:	20.04
Codename:	focal


 williepabon@williepabon-Macmini:~$ grub-install -V
grub-install (GRUB) 2.04-1ubuntu26.6
williepabon@williepabon-Macmini:~$


 Thanks for the help.

---

### Post by oldfred on 2020-11-02
Moved to Apple sub-forum.

Do not know Mac, but with PC and UEFI, it is escape key between Vendor's logo & start of grub. Timing often an issue.

You can in grub set menu to always show in grub's settings by changing to menu.

I changed mine to always show menu:
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/default/grub [/COLOR]
# If you change this file, run 'update-grub' afterwards to update 
# /boot/grub/grub.cfg. 
# For full documentation of the options in this file, see: 
#   info -f grub -n 'Simple configuration' 

GRUB_DEFAULT=0 
GRUB_TIMEOUT_STYLE=[COLOR=#ff0000]menu[/COLOR]

[/FONT]
```

---

### Post by williepabon on 2020-11-03
**fred:**

Thanks for answering. Your suggestion above I tried, but it didn't work for me. Just to mention, I had Ubuntu 18.04 in the same hardware and didn't have this problem. Has there been a change in grub that I should be aware of?

---

### Post by oldfred on 2020-11-03
There have been some updates to grub2.
But did not think related to your issue. But may be different for a Mac.

Do you only have one install.
Grub menu does not show by default if just Ubuntu as it knows that is the only thing you want to boot.

I have turned off os-prober as I have some obsolete installs and only add the entries I want in 40_custom.
Not sure if adding an entry to 40_custom would make a difference or not.

---

### Post by ajgreeny on 2020-11-03
I like to see the grub menu for a very short time even though I use a single boot system, and it is easier than stabbing at Esc when powering on the machine which does not always seem to work as it's supposed to on a UEFI system.

I have edited my /etc/default/grub file to the following lines
```
GRUB_DEFAULT=0
#Next line will make the countdown time show the menu
GRUB_TIMEOUT_STYLE=menu
#Next line changed from 0 to x for x second delay
#GRUB_HIDDEN_TIMEOUT=2
GRUB_TIMEOUT=2
#Next line changed from true to false to allow delay countdown to show
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_DISTRIBUTOR="Xubuntu-20.04" [COLOR="#0000FF"]##Ignore this as it just means I see Xubuntu in grub rather than the Ubuntu default[/COLOR]
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
This means I see the grub menu for 2 seconds at every boot, but as I boot only when a new kernel appears, that is not very often and is of little importance to me in terms of the time taken.
 
After editing the file don't forget to run command ```
sudo update-grub
``` or none of the edits will be implemented.
Like many other users, I also know nothing about Apple hardware, but I assume that grub will work the same there as it does in other machines.

---

### Post by williepabon on 2020-11-03
[**[COLOR=#C61919][B]ajgreeny**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=27747"):

Thanks for the suggestions above. Did them but apparently, boot sequence stops (since it doesn't show, I can't know for sure) and I have to turn off the pc and boot using Mac boot loader. Any other suggestions or ideas are very much welcome.

---

### Post by ajgreeny on 2020-11-03
When you ran the ***sudo update-grub*** command, and it is essential you do so, what was the output?

Normally you should see something like
```
sudo update-grub
[sudo] password for ajgreeny: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found background image: grub-zerus.png
Found linux image: /boot/vmlinuz-5.4.0-52-generic
Found initrd image: /boot/initrd.img-5.4.0-52-generic
Found linux image: /boot/vmlinuz-5.4.0-51-generic
Found initrd image: /boot/initrd.img-5.4.0-51-generic
Adding boot menu entry for UEFI Firmware Settings
done

```
which shows that it is finding the kernels installed and adding them to the grub menu.
If you do not see a similar output it may mean that your Apple hardware is using something other than grub to boot the system but what that might be I have not the faintest idea as Apple hardware and OSs are unknown to me.

---

### Post by williepabon on 2020-11-03
[B]ajgreeny:
[/B]
This is what I get when I run update-grub:

```
williepabon@williepabon-Macmini:~$ sudo update-grub
[sudo] password for williepabon: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-52-generic
Found initrd image: /boot/initrd.img-5.4.0-52-generic
Found linux image: /boot/vmlinuz-5.4.0-51-generic
Found initrd image: /boot/initrd.img-5.4.0-51-generic
done
```

If there any other thing missing? Thanks

---

### Post by ajgreeny on 2020-11-03
OK, so the only real difference between your output and mine is the ***Adding boot menu entry for UEFI Firmware Settings*** that I see but you don't.

Perhaps this is a result of how Apple hardware deals with UEFI but I'm afraid I will have to leave this or it will be a case of "The blind leading the blind", ie, neither of us knows enough about grub, UEFI or Apple hardware's implementation of grub.

---

### Post by williepabon on 2020-11-03
**ajgreeny:**

OK. Thank you for your patience in dealing with this issue. I will keep looking for a solution. If I find it, I will post it here. Thanks again.
wp

---

### Post by sebadamus2 on 2020-12-01
> **williepabon said:**
> **ajgreeny:**

OK. Thank you for your patience in dealing with this issue. I will keep looking for a solution. If I find it, I will post it here. Thanks again.
wp

Same here, just installed Focal on MacBookPro 8.2 and there is no way to show the grub menu at boot, even tried with grub-customizer thinking it will do something else, but nop :-/
Seems to work GRUB_DEFAULT=(the number of your entry 0,1,2,etc) but not showing menu.
I have default UEFI mac boot, no rEFit... maybe with rEFit will help, but kind of will enjoy as it is until trying again and break something :-p

---

### Post by oldfred on 2020-12-01
I thought refit was not supported anymore.

Better to use rEFInd
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by williepabon on 2020-12-17
[SIZE=4]**sebadamus2:**[/SIZE]

In another forum I found the following suggestion to modifly grub, and it worked for me.

1) set GRUB_TIMEOUT=5
2) uncomment GRUB_TERMINAL=console

Then, sudo update-grub
Try it to see if it solve your problem.
wp

---

