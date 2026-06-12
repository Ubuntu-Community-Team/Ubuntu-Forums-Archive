---
title: "ahhhh! Cant Login as the Admin"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2005-08-10
Hey, I Installed Ubuntu Today... but am unable to login as root or install any programs (like limewire for the music obv lol) cant live without the music. Please Help me... i need it.

Thanks Alot
~Lance

*edit... i get this every time i try to do something that requires me to type my admin password

Failed to Run .....whatever
Child Terminated with 1 status

---

### Post by tophfisher on 2005-08-10
Have you used the sudo command? Try sudo -s

Ubuntu does not have the root account enabled by default for secuirty reasons. Instead you use sudo to execute only the app you need. Safe computing baby!  \\:D/

---

### Post by Ubunted on 2005-08-10
There is no admin account. You type sudo before any commands to install things then enter your password. for example:

```
sudo apt-get install flashplayer-mozila
```

And so on.

---

### Post by noob_Lance on 2005-08-10
um.... ok well that helps and it dosnt lol... i cant even change the TIME on my CLOCK! 

where or how do i do this sudo... thing???? if anyone has msn and can help me.... ADD ME! lol

silver_suicide_rider @ hotmail.com

Thanks

---

### Post by aysiu on 2005-08-10
I don't know about the child stuff, but this may help you for the root stuff:

[https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29)

---

### Post by noob_Lance on 2005-08-10
riiiight.... this is still gettin me no where... because ive got no clue at what im doin here. is there any way to actually log in as root? or activate it?

---

### Post by aysiu on 2005-08-10
[QUOTE=noob_Lance]riiiight.... this is still gettin me no where... because ive got no clue at what im doin here. is there any way to actually log in as root? or activate it?[/QUOTE] All right. Take three deep breaths, and calm down. Can't you see people are trying to help you? Okay, first of all, let's try to help you accomplish your end-goals. Right now, you think you need root to accomplish those goals. Let's try doing it with sudo first. If you try sudo, and you don't like it, there's a way to enable root, but there was a reason root was disabled to begin with--security reasons.

Okay. Let's start with Limewire. Do you know what a command-line is? Do you know how to open a terminal?

If so, follow these instructions, in this order:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)
[http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

If you have problems, let us know.

---

### Post by noob_Lance on 2005-08-10
can i enable root then disable it once im done lol

---

### Post by noob_Lance on 2005-08-10
root2 is not in the sudoers file.  This incident will be reported.

thats what i got...

---

### Post by aysiu on 2005-08-10
Who's root2? Is that the username you created when you installed Ubuntu? Or did you add it later?

---

### Post by noob_Lance on 2005-08-10
i dont know wtf is goin on lol... its the one i can log in as. when i try jsut root. it says the admin cant login thru that login screen.. .so yes i guess this is the one i created on install

---

### Post by KingBahamut on 2005-08-10
to enable root account 

sudo passwd root - set new root password. 

Where the heck did you get root2 from?

---

### Post by KingBahamut on 2005-08-10
noob, try to calm down.....

---

### Post by noob_Lance on 2005-08-10
*calm* its not letting me use sudo as im not a member of the sudoers file :S someone honestly walk me thru it in english please lol

---

### Post by aysiu on 2005-08-10
[QUOTE=noob_Lance]*calm* its not letting me use sudo as im not a member of the sudoers file :S someone honestly walk me thru it in english please lol[/QUOTE] If what I understand you're saying is true, something's wrong with your installation. A typical installation works this way:

Select language
Partition, yada yada yada
Username
Password
Installation stuff
Grub
Reboot
Lots of stuff on the screen

You log in with username.

Now, if you followed that route, there should be only one user, no other users (not even root). That one user, though, should already be in the sudoers file.

So, you're telling me there's only one user you created for your Ubuntu installation and that user's name is *root2*?

---

### Post by noob_Lance on 2005-08-10
im going to try to reinstall this friggin OS... i thought ubuntu was supposed to be EASY! :@ lol be back in a bit lol

---

### Post by aysiu on 2005-08-10
[QUOTE=noob_Lance]im going to try to reinstall this friggin OS... i thought ubuntu was supposed to be EASY! :@ lol be back in a bit lol[/QUOTE] Anything new's going to seem a little tough at first. When I first started using Ubuntu, I hated sudo, but it's really grown on me. Now, I never use root. I wouldn't say your situation is typical, though. Usually newbies hate or are confused by sudo, but their first users are usually in the sudoers file. Well, let us know how it goes the second time around.

---

### Post by noob_Lance on 2005-08-10
ok good news... i did jsut f up my installation... after i reinstalled... it all is good once again. Now i have a big question... i have a TON of music and pics on my other partition.... an NTFS. is there ANY way i can get those files onto this partition... please help... thanks

~Lance

---

### Post by noob_Lance on 2005-08-10
hehe nvm... i got it =D

---

### Post by aysiu on 2005-08-11
[QUOTE=noob_Lance]hehe nvm... i got it =D[/QUOTE] So you're able to sudo and all that? Congratulations.

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by noob_Lance on 2005-08-11
lol thx... but i already got it haha. but um... heres a goooood question. i have an MD player (sony mini disk) if i wanted to transfer songs to it... how would i go about that one lol...

---

### Post by MBHockey on 2005-08-11
Hey guys...this is my first time with any flavor of linux, and after repartitioning my drive so i can dual boot Ubuntu and Tiger, i am experiencing the same thing the original poster is.

I can log in to my user account fine when i log into Ubuntu, but if i try to run anything from System --> Administration (and then i enter the password i use for my user login) it throws that same error: 

> Failed to run network-admin:
 Child terminated with 1 status 

So I opened up Terminal, and tired to run "sudo -s" but it throws this error:

> Failed to run network-admin:
mike is not in the sudoers file.  This incident will be reported. 

The user name for my Ubuntu login is mike, and the password i use is not working in Terminal either (not that i'd expect it to).

I'm hoping this isn't a borked installation.  I'm running Ubunto 5.0.4.  

Can i just use vi to edit the sudoers file to add mike as a user?  If so, where is that sudoers file located?  I have edited that file before on MacOS X, but i can't remember where it was.

Thanks.

Edit:  Seems like quite the catch-22.  I need root/sudo access to run 'visudo' so i can add myself to the file, heh, any way around this?

---

### Post by noob_Lance on 2005-08-11
hey MB, what i did was i jsut reinstalled the whole Ubuntu OS and made my username ryder18 (passion and age haha). my guess is you did the same as myself and messed up at the username and password section. So if anything, reinstall and try again... it worked for me =D

---

### Post by varunus on 2005-08-11
I don't know if you can do this on the mac version, but on the x86 version of Ubuntu, you can choose "recovery mode" at the grub bootloader.  This lets you log in as root automatically at a console prompt.  Execute the following command once you do this:

visudo

Press the "INSERT" key, then move down to the end of the document, and add the following line at the end:
```
yourusername  ALL=(ALL) ALL
```

then press ESCAPE, then type (exactly): "SHIFT-SEMICOLON" (ie colon), W, Q, enter.

Then reboot and you should be fine.

---

### Post by MBHockey on 2005-08-11
[QUOTE=varunus]I don't know if you can do this on the mac version, but on the x86 version of Ubuntu, you can choose "recovery mode" at the grub bootloader.  This lets you log in as root automatically at a console prompt.  Execute the following command once you do this:

visudo

Press the "INSERT" key, then move down to the end of the document, and add the following line at the end:
```
yourusername  ALL=(ALL) ALL
```

then press ESCAPE, then type (exactly): "SHIFT-SEMICOLON" (ie colon), W, Q, enter.

Then reboot and you should be fine.[/QUOTE]

Thanks...i was able to boot to single user mode, on an absolute guess, by typing 'Linux single' at the yaboot loader...i wasn't automatically logged in as root though, so i logged in with my password, which it accepted.  i quickly added 'mike' to the sudoers file (the text editor was quite more user friendly than vi, btw) saved it, and rebooted.

all is working well now.  
thanks again

---

### Post by aveline on 2005-08-11
[QUOTE=noob_Lance]hey MB, what i did was i jsut reinstalled the whole Ubuntu OS and made my username ryder18 (passion and age haha). my guess is you did the same as myself and messed up at the username and password section. So if anything, reinstall and try again... it worked for me =D[/QUOTE]
 next time just use visudo .. afaik its the best way to edit the SUDOers file and it says that if you a text editor & try to edit the file any other way except when in single user mode.

its an easy lil program to use and has nice lil help file.  just do on the cmd line:

info visudo 

that will give you a fairly more up tod ate help file... info files are *usually* more up to date than man pages i found.

hth
aveline

---

