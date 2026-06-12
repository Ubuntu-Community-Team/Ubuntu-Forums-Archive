---
title: "This sounds crazy right?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by BAS54 on 2007-05-08
Hi guys. First post .
Installed Dapper Drake 2.14.1.  No problems. Plan to dual boot so disconnected second HHD running W98se.
Linux loads okay. Explored everything. 
Modem not dialing out. Read countless post . Followed links etc. Tried everything I could find on the problem.
No luck. So decided to reconnect the second HD  check out the reboot. Windows loaded.
I've set everything up in Bios and jumpers etc. Got a brilliant Bios menu too.
Anyway my problem is this.  I can't access anything in a Terminal.
It's not that I am stupid and I printed out most of the Help pages in Gnome, but I'm missing one click some place. 
 Code entries that are written on these postings must assume a given. The way to get there.
I start with a $ with a blinking curser. 
I type sudo with a space then the given code and get a new line saying 'no command' or words to that effect
Once I was told, " this is a directory" . Once I was told 'No authorization"
I feel so stupid but just ca't figure it. Of course, in Windows I'd blah blah blah. 
Just joshing!
 Someone please set me straight.
BAS.

---

### Post by gjtoth on 2007-05-08
I'm no console expert... not be any stretch of the imagination :) however, you might get more responses if you were a little more specific in the commands you're attempting to execute.  "sudo ___________ " doesn't tell much.

Just a thought.

---

### Post by Terl on 2007-05-08
What exactly are you trying to do?

Are no commands working?  Or is it the code you are trying from the forums?

---

### Post by BAS54 on 2007-05-08
Thanks for the come back fellows.

Name any command after sudo.

I installed Ubuntu on the weekend and am just seeing where everything is etc. 
I was trying various ways regarding the dial up/modem connection business. Things appeared to go through as far as the actual connecting. Then stp. No panic there.I'll chase it up later. I have this second computer for the net. 
So I thought I would ckeckout the Bootup sequence setup and as I said I have quite a number of downloaded postings. So tried to enter some of the codes . Hence the post.
 BAS

---

### Post by BAS54 on 2007-05-08
Back.  
Maybe if you wrote click by click how you would get from Desk top to Bootup menu for example, it would hit me.
BAS

---

### Post by Terl on 2007-05-08
Are you trying to leave the graphical environment and go into a virtual terminal?  Is that what you mean by "boot up menu"?

You can do a great deal with just the terminal available under your accesories section in the application menu.  I would caution you that you do need to be careful with sudo.  You can do some serious damage if you are not careful.

Is something not working?  It sounds like you might be trying to get your modem to work.  It is difficult to tell you what to do when we don't really know what you want to do.

---

### Post by BAS54 on 2007-05-08
Thanks TERL.

Forget the modem thing. That is down the line .

I have two HDs And loaded Ubuntu inderpendantly. So I assumed it made no entry in it's bootup menu as regards W'98. 
So, I read where such an entry for another OS could be entered into the menu to ignore at boot up. Because when I did reconnect the W98 drive, that is what loaded. 
  
I just assumed that to deal with any code one would have to enter via the terminal.

Look, Thanks a lot anyway. I'll do some more reading up.

BAS

---

### Post by steve.horsley on 2007-05-08
Are you trying to edit the list of operating systems offered at boot for some reason? If so, the file that configures this is /boot/grub/menu.lst which is a text file. 

You can view it by navigating there with nautilus (the equivalent of Windows Explorer) - click Places->Home (in the top bar), then click Up twice (top of the file explorer window), then double-click the  **boot** folder and then double-click  the **grub** folder. Then double-click the **menu.lst** icon.

The text command to achieve the above is:
**gedit /boot/grub/menu.lst**
which is why people prefer to give text commands over lengthy click this, click that essays. You can get a command prompt by clicking Applications->Accessories->Terminal (if I remember correctly). You can paste commands in from your web browser (when you get teh network working) which removes typing errors, and you can copy/paste the output back to tell people what happened. 

If you understand the file and want to edit it, this is the command to do so:
**gksudo gedit /boot/grub/menu.lst**

Please don't ever say something "doesn't work" - the better description of what happened you can give, the better other people can understand what's going on.

---

### Post by Terl on 2007-05-08
Oh!  Ubuntu installer is very good.  I have 2 hard drives also.  When you disconnected the win98 disc Ubuntu did not know anything about it so, yes, no loader entry is there for windows98.  Normally you would have just left the windows drive as the "main drive" and then installed Ubuntu on the second.  It would have seen windows98 and set your loader up for you.

If you are very new, here is how I would fix it...just easier to me.  I would put the windows drive back as the main drive, move the ubuntu as the second.  I would go ahead and reinstall ubuntu and let it put the boot loader (GRUB) on your main drive.  When you restart you should have a choice of Ubuntu or windows (windows will be last on the list).  

This is fixable without a reinstall but will take editing of your grub files.  Steve gave good advice above.  Know what you are doing first before you modify the grub files or you may not be able to boot into anything until you fix whatever broke.  

As for the terminal, you can do a lot with the terminal in Gnome (your desktop) but some things do require the X server to be shutdown first.  To get to a virtual terminal you can hit Control-Alt-F2 and to come back to the graphics (if the xserver is still on) hit Control-Alt-F7.  If you are new to Linux, I would recommend looking around for tutorial on the commands.  There are lots of them.

---

### Post by Tomosaur on 2007-05-08
It sounds like you've entered into a virtual terminal. Is the whole screen one big terminal? If so, hit ctrl+alt+f7 and see if that brings you back to the gui. Alternatively, type 'sudo reboot' and wait for the machine to reboot. You can access the terminal as any other GUI application you see, it's in the Applications > Accessories menu.

If the problem is that no commands are working, please type the following in the terminal:
```

echo $PATH

```

The output should look something similar to this:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

If the output you get is not similar to that, then there's your problem - the directories listed above are where your machine looks to find programs when you type a command in the terminal. You need to add the following line to the end of your .bashrc file in **your** home directory:

```

export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

You should be able to do this by rebooting your machine and going into recovery mode, and typing:
```

echo "export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" >> /home/<your user name>/.bashrc

```

Replace <your user name> with whatever your username actually is.

If i've totally misunderstood your problem, then feel free to ignore :P

---

### Post by BAS54 on 2007-05-08
Got it

Thanks very much all. Truth be known I don't know the jargon enough. .But no excuse.
Point taken. I'll write everything down in future. 
Steve Horsly, I can follow you. I didn't know that path. 
 Steve,Teal and Tomosaur , full marks. 


Post closed.Bas

---

