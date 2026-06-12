---
title: "Problems Installing Ubuntu!"
date: 2005-07-25
forum: Absolute Beginner Talk
---

### Post by mattiouk on 2005-07-25
Hi!  I'm new here, so I may ramble on slightly!  Apologies in advance!  ;-) 

OK, basically I have a USB Keyboard, when trying to install Ubuntu  I am prompted to type a root (I think this is the term) username and password but when I try to type this in, nothing happens - there is no response on the screen and no keys are recognised. As a result using the automatic installation, I can't carry on installing Ubuntu which is quite a large problem for me.  When I tried doing this in the advanced set up, I could bypass this section of the installation, however when I then logged in, it wouldn't let me change any settings at all as I needed the password I had to type in?

The thing I don't understand is, that the keyboard is recognised by Ubuntu, as it lets me alter and move through the menus, so why can't I enter any characters for the password???  :???: 

Any help would be really great.

Matt

p.s. - Is there a way I can also configure the GRUB boot loader thing, to have windows at the top of the list, as the default so this will load as other members of  my family prefer windows and aren't happy with GRUB bootloaders having LINUX at the top!  :-|

---

### Post by poofyhairguy on 2005-07-25
[QUOTE=mattiouk]
p.s. - Is there a way I can also configure the GRUB boot loader thing, to have windows at the top of the list, as the default so this will load as other members of  my family prefer windows and aren't happy with GRUB bootloaders having LINUX at the top!  :-|[/QUOTE]


Yes: 

[http://www.ubuntuforums.org/forumdisplay.php?f=77](http://www.ubuntuforums.org/forumdisplay.php?f=77)

Its here:

[http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb](http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb)

As far as the other thing, did you turn numlock on?

---

### Post by fyrefly on 2005-07-26
[QUOTE=mattiouk]Hi!  I'm new here, so I may ramble on slightly!  Apologies in advance!  ;-) 

OK, basically I have a USB Keyboard, when trying to install Ubuntu  I am prompted to type a root (I think this is the term) username and password but when I try to type this in, nothing happens - there is no response on the screen and no keys are recognised. As a result using the automatic installation, I can't carry on installing Ubuntu which is quite a large problem for me.  When I tried doing this in the advanced set up, I could bypass this section of the installation, however when I then logged in, it wouldn't let me change any settings at all as I needed the password I had to type in?

The thing I don't understand is, that the keyboard is recognised by Ubuntu, as it lets me alter and move through the menus, so why can't I enter any characters for the password???  :???: 

Any help would be really great.

Matt

p.s. - Is there a way I can also configure the GRUB boot loader thing, to have windows at the top of the list, as the default so this will load as other members of  my family prefer windows and aren't happy with GRUB bootloaders having LINUX at the top!  :-|[/QUOTE]
 Re USB Keyboard: Make sure you have USB set to boot in your bios.

---

### Post by mattiouk on 2005-07-26
I tried the bios, it was already set, and also I tried toggling number lock but there was no success.  ](*,) 

buy...  :roll:  I decided for some reason to bypass this part of the setup (in expert mode) and the rest of Ubuntu installed really well, its just now there is no root password.  So if I didn't enter anything, will it be set to a default password which I can enter?  Is there some way to overwrite this????

Please Help!

Sorry to be so stupid here.

Matt

P.s. I downloaded that GRUB changer but how do I install it???  :-x   I'm feeling pretty dumb here, sorry.

---

### Post by fyrefly on 2005-07-26
[QUOTE=mattiouk]I tried the bios, it was already set, and also I tried toggling number lock but there was no success.  ](*,) [/QUOTE]

Tempoarily, until you can make sure hotplug is working in Ubuntu, try a PS2 keyboard. This will be a temporary fix at least to log in and checking the configuration. 


[QUOTE=mattiouk]I decided for some reason to bypass this part of the setup (in expert mode) and the rest of Ubuntu installed really well, its just now there is no root password.  So if I didn't enter anything, will it be set to a default password which I can enter?  Is there some way to overwrite this???? [/QUOTE]

When you try to install / open anything that requires root, type in "sudo" and your user password. I was using Fedora Core 3 before Unbuntu [just installed 2 days ago and loving it so far], so it took a few minutes for me to realize I didn't require a root password. :P

[QUOTE=mattiouk]P.s. I downloaded that GRUB changer but how do I install it???  :-x [/QUOTE]

If you are using Grub for a multiple OS partitions, it should have installed while installing Ubuntu. I keep a windows partition for some games and the Ubuntu installation recognized the partition without any problems and at initial boot up I have the option to boot into of Ubuntu or windows. 

Did you have another OS partition when you were installing Ubuntu or is it something you are adding now?  

[QUOTE=mattiouk] I'm feeling pretty dumb here, sorry.[/QUOTE]

Don't feel dumb, I'm still new to linux and struggle with a few things. We all start somewhere and without help from these  forums I would have been lost. :)

---

### Post by poofyhairguy on 2005-07-26
[QUOTE=mattiouk]I tried the bios, it was already set, and also I tried toggling number lock but there was no success.  ](*,) 

buy...  :roll:  I decided for some reason to bypass this part of the setup (in expert mode) and the rest of Ubuntu installed really well, its just now there is no root password.  So if I didn't enter anything, will it be set to a default password which I can enter?  Is there some way to overwrite this????

Please Help!

Sorry to be so stupid here.

Matt[/QUOTE]

How could you know what to do?

Does this help?

[http://www.ubuntuforums.org/showthread.php?t=51371&highlight=user+password](http://www.ubuntuforums.org/showthread.php?t=51371&highlight=user+password)

> P.s. I downloaded that GRUB changer but how do I install it???  :-x   I'm feeling pretty dumb here, sorry.

Don't feel dumb, do this after you set up the user account.

sudo dpkg -i grubconf_0.5.1-4ubuntu2_i386.deb

---

### Post by mattiouk on 2005-07-26
Thanks for teh replies!  :grin: 

Unfortunately... I have tried all the suggestions, sudo as a password, just hitting enter and the related links in the linked threads but still no joy!

I googled it... and it told me to try...

sudo passwd root

so I did, but then it asked me for the password and the computer did the exact same thing as it did during installation, all the letter and number keys froze and I couldn't type in anything!!!  All I could do was hit enter, to be told that i had entered the wrong password!  :? 

Any suggestions?  Do you think a PS2 keyboard would solve this?

Is there a way to set a new root password if another one is already set?

Thanks for all the help.

Matt

---

### Post by poofyhairguy on 2005-07-26
[QUOTE=mattiouk] Do you think a PS2 keyboard would solve this?[/QUOTE]

Yes. Try to borrow one for this.

> Is there a way to set a new root password if another one is already set?

Thanks for all the help.

Matt

yes. Boot into recovery mode and do the password command thing.

---

### Post by fyrefly on 2005-07-26
[QUOTE=mattiouk]Unfortunately... I have tried all the suggestions, sudo as a password, just hitting enter and the related links in the linked threads but still no joy!Matt[/QUOTE]

Maybe I'm reading this wrong ... are you typing "sudo" as your password?

Say your user ID was "matt", password is "mypassword"

Open the terminal and type [as an example]

[COLOR=DarkGreen]sudo update-manager[/COLOR]

the password prompt will display in the screen, type:

[COLOR=DarkGreen]mypassword[/COLOR]

hit enter and you are set to go.


To change the root password, in the terminal type:

[COLOR=DarkGreen]sudo passwd root[/COLOR]

---

### Post by mattiouk on 2005-07-27
Ok... 

I rebooted into Recovery Mode, and then typed: -

sudo passwd root

and the next reply I got instead of a password prompt was: -

matthew is not in the sudoers file.  This incident will be reported?  :| 

Any suggestions???

---

### Post by fyrefly on 2005-07-27
Did you create another user? Sounds like the user name you are using wasn't given sudo access.  I'm not sure if this will help, but here's a Ubuntu Guide, "How to gain root user access without login?"

[http://ubuntuguide.org/4.10/index.html#gainrootwithoutlogin](http://ubuntuguide.org/4.10/index.html#gainrootwithoutlogin)

---

