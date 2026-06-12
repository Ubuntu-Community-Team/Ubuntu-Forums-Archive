---
title: "Lost My Password Already!"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by Shalaw on 2005-12-28
I had no trouble getting ubuntu on my Compaq Presario, but when it came up Username and then password, I can't get past it.  I keep getting the message: Incorrect username or password.  Letters must be typed int he correct case.  I must not have written them down the same as I typed one of them.  What now?  I looked up "lost password" and I tried to edit the kernal root@ but I haven't had any results from that either.
Anyone out there that can give me better directions?
Any help would be appreciated.
Thanks 
Shalaw

---

### Post by narcolept on 2005-12-28
If remembering the case doesn't work, you can by hitting escape to enter the bootloader, hitting e, selecting the kernel line, hitting e again to edit, and appending init=/bin/sh, then booting that kernel. It will then drop you to a plain shell.  You'll need to remount slash with the command

```
 mount -o remount,rw / 
```

and then

```
 mount -a 
```

Then you can change the passwd with

```
 passwd <username>
```

and then reboot.

---

### Post by Shalaw on 2005-12-29
When I hit esc and get into my Kernels there are 3 of them which do I edit?

---

### Post by narcolept on 2005-12-29
It doesn't amtter, because you'll only be doing it once.  Your cursor will be on your default kernel.

---

### Post by Shalaw on 2005-12-29
I'm just going in circles. The Grub loading takes me to the 3 kernals e takes me to second screen and kernel is second on list. e takes me to 
grub edit> kernel  /boot/vmlinuz-2.6.12.9-386 root =/dev/hda1 ro quiet splash
when i put the init thing on it, it make the circle again to the logon  where I don't know the password.

---

### Post by Shalaw on 2005-12-29
I'm not getting to  a place to put a new password in.
I am just being rerouted to the logon and it still doesn't accept my username or password.

---

### Post by arpanaut on 2005-12-29
Here, give this a try from the wiki:

[https://wiki.ubuntu.com/LostPassword](https://wiki.ubuntu.com/LostPassword)

maybe these directions are a little clearer.
There is a way to do this through The recovery mode.... Try a search on that

GL

---

### Post by narcolept on 2005-12-29
[QUOTE=Shalaw]I'm just going in circles. The Grub loading takes me to the 3 kernals e takes me to second screen and kernel is second on list. e takes me to 
grub edit> kernel  /boot/vmlinuz-2.6.12.9-386 root =/dev/hda1 ro quiet splash
when i put the init thing on it, it make the circle again to the logon  where I don't know the password.[/QUOTE]

You would append init=/bin/sh to this line, hit enter, and then press 'b' to boot, then follow the instructions above.

---

### Post by Shalaw on 2005-12-29
Ok Now I'm beginning to think that there was nothing wrong with my password, because I've done all of the above got to the part where you put the password in twice. and it still doesn't work!
I get a authentication is busy message. and am put on the outside to log in/on again and I can't because it says I don't know my username or password  ......I'm not typing them right?  I'm not even sure what they are anymore.

---

### Post by Shalaw on 2005-12-29
It's 328 in the morning here so I'm headed off for bed.  I'll check in, in the morning to see if there is anything else I can try, but right now I'm not with it..
Thanks for all the help everyone.
See you tomorrow.
Shalaw

---

### Post by Shalaw on 2005-12-29
Ok I'm awake now.  I'll retry all last night's advise again.  I'm hoping it was just my head that wasn't working.:???:

---

### Post by Shalaw on 2005-12-29
pressed escape at grub.
pressed e at kernel
moved fromroot (hd0,0) down to kernel  
pressed e
got
grub edit> kernel  /boot /vmlinuz-2.6.12-9.386 root=/dev/hda1 ro quiet splash
added
init=/bin/sh
hit enter
typed
boot 
hit enter
This openned ubuntu and started loading modules.  Took me to:
Checking root file system:
has been mounted 30 times without being checked, check forced.
It went through alot and then to username and password  logon page.
next try

---

### Post by Shalaw on 2005-12-29
Turned off computer
Turned on computer
pressed esc at grub line
Got
Unbuntu, kernel
pressed e
got root, kernal, initred, savedefault,boot
went to kernal
pressed e
got 
grub edit> kernel  /boot/vmlinuz-s.6.12-9-386 root=/dev/hda1 ro quiet splash
added
rw init=/bin/bash
pressed enter
then pressed b
got a lot of lines then page loading modules then 
root@(none):/#
typed in 
passwd
got
Enter new UNIX password:
typed
SamHill
no stars showed up 
it said retype new UNIX password:
typed
SamHill
got 
passwd: Authentication token lock busy
root@(none): /#
booed
back to logon no passwords work   @##@#@!

what now?

---

### Post by jml75 on 2005-12-29
Shalaw, look at these instructions I found at : [https://wiki.ubuntu.com/LostPassword](https://wiki.ubuntu.com/LostPassword)

1 - Turn your computer on. 
2 - Press ESC at the grub prompt. 
3 - Press e for edit. 
4 - Highlight the line that begins kernel ........., press e 
5 - Go to the very end of the line, add rw init=/bin/bash 
6 - press enter, then press b to boot your system. 
7 - Your system will boot up to a passwordless root shell. 
8 - Type in passwd <username>. Set your password. 
9 - Type in reboot.

What you did is good except for two things...

- First, take a look at step 5, it mentions rw init..., I think the rw is very important or else the root file system will be locked in read only state so it will be impossible to change any thing so impossible to reset a password since it is stored on the file system itself in an encrypted file. The rw stands for ReadWrite.

- Second, when you get to the prompt 'root@(none):/#', you are logged in as root so if you issue the command passwd and then press enter, you are trying to change the password for the system admin user 'root'. So to be able to change the password for your own user, do the command like it is shown at step 8 : passwd <username>, your own username.

If you want to verify your username, type the command users, it will list you on the screen the list of all available normal users.

Most likely, the reason why the command passwd alone does not work is because it would allow anyone to change the root password way to easily and this is something you definitely don't want to happen.

Hope it helps! :smile:

---

### Post by Shalaw on 2005-12-29
Thanks I'll try it all again

---

### Post by jml75 on 2005-12-29
Actually I tested it again and at step 5 the rw is of the most importance because if you do not put rw, it will give you the message that you got saying that the tocken is locked or something, I tried both and with the rw and without the rw and it is really as I told you.

But with the rw it IS possible to change the root password. I thought it would not be but it is. So when you are at the root@(none)... prompt if you type the passwd command, it will change the password for user root only, the normal user will remain with the original password and you'll be stuck again not being able to log in.

So passwd <username> is what you need.

Hope it helps!
:cool:

---

### Post by psusi on 2005-12-29
Do NOT mess with adding init=/bin/sh in grub, simply choose the rescue option from the menu and login as root with no password, then use the passwd command to set your password.

---

### Post by jml75 on 2005-12-29
Psusi,

There is no problem putting rw init=/bin/bash in grub if it is throught the edit function of the grub console...

No one ever recommanded modifying the menu.lst with this option...

Simply typing e at the menu and e at the kernel line.

Works great, just tried it!

---

### Post by psusi on 2005-12-29
It is more difficult and more dangerous than simply choosing the rescue option from the existing menu, or hitting ctrl-alt-F1 when the system is already running to switch to a text console and login as root.  That's actually the easiest and safest thing to do.  Then you can hit alt-F7 to switch back to GUI and login with your new password right away.  

[QUOTE=jml75]Psusi,

There is no problem putting rw init=/bin/bash in grub if it is throught the edit function of the grub console...

No one ever recommanded modifying the menu.lst with this option...

Simply typing e at the menu and e at the kernel line.

Works great, just tried it![/QUOTE]

---

### Post by Shalaw on 2005-12-29
I still can't go in.  I get amessage 
Authenication token lock is busy
Then it goes back to 
root@(none):/#





So where am I when I am at this line?

---

### Post by psusi on 2005-12-29
mount -o remount,rw /

[QUOTE=Shalaw]I still can't go in.  I get amessage 
Authenication token lock is busy
Then it goes back to 
root@(none):/#
I[/QUOTE]

---

### Post by Taino on 2005-12-29
Follow this carefully, its from the wiki..

[https://wiki.ubuntu.com/LostPassword](https://wiki.ubuntu.com/LostPassword)

Lost Password?

When booting up press ESC at the grub prompt. Use the arrow keys to select the rescue mode option and press enter. This will boot the system in rescue mode and you should arrive at a prompt to either enter the root password, or press ctrl-d. There is no root password by default in ubuntu, so just press enter and you will be logged in as root.

Now you can reset your password with:

passwd <username>

The to switch to normal gui mode where you should be able to log in with your new password enter:

init 2
Last resort

If the above does not work ( i.e. because there IS a password on the root account and you don't know it ) then you can try this as a last resort.

CAUTION: Step 7 gives you a FULL ROOT SHELL! You can damage your system if not careful!

   1.

      Turn your computer on.
   2.

      Press ESC at the grub prompt.
   3.

      Press e for edit.
   4.

      Highlight the line that begins kernel ........., press e
   5.

      Go to the very end of the line, add rw init=/bin/bash
   6.

      press enter, then press b to boot your system.
   7.

      Your system will boot up to a passwordless root shell.
   8.

      Type in passwd <username>. Set your password.
   9.

      Type in reboot.

-------------------------------------

Do you know your "Username"?  or did you forget "Both" your "Username" and "Password"??

If you forgot both things then that is a different situation than just recovering a lost "Password".

---

### Post by Shalaw on 2005-12-29
Thanks I know my username.  So I'll try this first.
I've come up with Error: Temporary failure in name resolution.         [fail]
root@ubuntu:~#

---

### Post by Shalaw on 2005-12-29
[QUOTE=Taino]Follow this carefully, its from the wiki..

It WORKED!!!!!:KS :KS 


Thank you so much!!!
I was just about to throw in the towel.;) 
Thank you.
I'm going to copy this in case the web page disappears.:p

---

### Post by Taino on 2005-12-29
[QUOTE=Shalaw]It WORKED!!!!!:KS :KS[/QUOTE]

Way to go! :mrgreen: =D> \\:D/

Yeah, the following it "Carefully" part is very important. ;)

---

### Post by Shalaw on 2005-12-29
Wow  You should see all the stuff on my computer!:p 
But I called my internet provider and they don't know how to hook me up
to go here from ubuntu.  In fact they didn't seem to know if it was legal to go through a public internet server.  How else would you connect to the internet?:confused:

---

### Post by jml75 on 2005-12-29
Good for you Shalaw!

What is your internet connection type?

By the way, your provider tech is a bit lunatic if he thinks that it would not be legal... My gosh, how can people be so ignorant!!! Thinking it would not be illegal to go online with linux is very strange. What do they think?  That the internet is owned by M$? If it was the case, could they explain me how all of thoses linux web server are able to be online? And how all of us linux users are connecting to the net?

I think that they just don't want to have to help you with your connection...

Poor them!

Ignorance is one of humanity's tragedy!

Have a nice one!:razz:

---

### Post by Shalaw on 2005-12-29
We just installed High speed or Ultra high speed, but I think I could still use the kids phone for dial up if Ubuntu needs to be on dial up.

---

