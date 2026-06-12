---
title: "Virtualbox."
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2007-09-19
Hi again. Always simple problems.( Not like AutoCad which is still excellent!)

Installed Virtualbox tonight, the Edgy .deb file.

Applications>System Tools>Innotek VirtualBox> Click.

I thought I'd set it up right. Hmm. VirtualBox gui.

Ubuntu 2 (powered off) 

Start.

Black screen with stuff. OK. Some info about nothing much.

Next: this.... 


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

Anyone know what to do?

Thanks in advance.

Mike.

---

### Post by madcow72 on 2007-09-19
You have to add yourself to the vboxusers group in order to start up virtualbox.  This is from Innotek's website:

If you get a message saying "VirtualBox kernel driver not accessible, permission problem" when starting VirtualBox immediately after installation, make sure that your user account is a member of the vboxusers group. This group is created when VirtualBox is installed, but you will need to manually add all users to it who are to be allowed to run VirtualBox. The documentation accompanying your Linux distribution should provide information about how to do this. If not, the following should also work on most Linux systems. These commands should be run as the Administrator user from the command line.

```
# groups <login name>
[Shows a list of groups for that login name]
# useradd <login name> -g <first group in list> -G <second group>,<third group>,...,vboxusers
```

---

### Post by MichaelSM on 2007-09-19
Thank you, madcow72's Avatar  	
madcow72.

Hey! I actually went there in sudo (#) mode and made sure that I (michael) was on the list. Hang on ...

The # is missing because of latest trip ...

michael@michael-desktop:~$ sudo -l
Password:
User michael may run the following commands on this host:
    (ALL) ALL
michael@michael-desktop:~$ groups
michael adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
michael@michael-desktop:~$ useradd michael
useradd: user michael exists
michael@michael-desktop:~$ 

Looks like I'm there. Is there a need to go through the entire list?

Thanks for a swift reply.

Michael.

---

### Post by raijinsetsu on 2007-09-19
```
gpasswd -a michael vboxusers
```

---

### Post by MichaelSM on 2007-09-19
Is this what I was supposed to do?


michael@michael-desktop:~$ 
michael@michael-desktop:~$ gpasswd -a michael vboxusers
gpasswd: Permission denied.
michael@michael-desktop:~$ sudo -l
User michael may run the following commands on this host:
    (ALL) ALL
michael@michael-desktop:~$ 
michael@michael-desktop:~$ gpasswd -a michael vboxusers
gpasswd: Permission denied.
michael@michael-desktop:~$ 

Many thanks.

Michael.

---

### Post by raijinsetsu on 2007-09-19
Sorry... I assumed you'd insert sudo... LOL
```
sudo gpasswd -a michael vboxusers
```

Also... what's with the "sudo -l"??
Do you mean "sudo -i"?
You shouldn't use interactive sudo unless you're doing batches of root commands. Just use sudo, followed by the command you want to run.

---

### Post by jadoti on 2007-09-19
sudo gpasswd -a michael vboxusers

---

### Post by madcow72 on 2007-09-19
raijinsetsu is right!  That's the way to add yourself.  Also, in the future if you forget that command, you can always go System -> Administration->Users & Groups
Then click on "Manage Groups"->vboxusers->properties and then add your user to that group.

---

### Post by raijinsetsu on 2007-09-19
> **madcow72 said:**
> raijinsetsu is right!  That's the way to add yourself.  Also, in the future if you forget that command, you can always go System -> Administration->Users & Groups
Then click on "Manage Groups"->vboxusers->properties and then add your user to that group.

Eww... GUIs...
LOL

---

### Post by madcow72 on 2007-09-19
Yeah...sorry 'bout that!  Your way is wayyy faster!

---

### Post by MichaelSM on 2007-09-19
A sudden over-supply of welcome posts.! 

Back to an earlier one. result.

michael@michael-desktop:~$ sudo gpasswd -a michael vboxusers
Adding user michael to group vboxusers
michael@michael-desktop:~$ 

Does that look right? 

Still get the same error.

I don't know why I use sudo -l rather than sudo -i. Just something which I picked up being a relative newbie. 

You guys are great. It's just me I guess.

Mike.

---

### Post by ppietryga on 2007-09-19
Now log out and in, so the changes (adding you to vboxusers) take effect :)

---

### Post by MichaelSM on 2007-09-20
Hi. And thank you for that. When you said 'Log out and log in,' I thought you meant log out of vbox. You meant 'Restart your computer.'

All done. 
Windows xp install complete.

I am totally amazed by the whole shooting-match. It's actually quite frightening .....

I have a Windows box for spare, which has had anything to do with Internet disabled, which I use for accounting etc.It never gets near the Internet!

So, with THIS Edgy box, I assumed the XP install with Virtualbox would require me to set up an Internet connection with XP. Jesu Christo! Just for fun I hit Internet Explorer and next thing you know I'm on the WEB! Scary!

That was NOT! meant to happen!!!

Naturally I'll disable the connection to the web. Don't wanna know about it, ever, with XP.

Otherwise;

VBOX I cannot  make the XP window fill the screen ( I have a 22-inch lcd). Not a major issue.

OK. The mouse pointer only works in the VBox window. There is an option for 'Control/Right' which should enable the  mouse pointer to move outside the VBOX parameters. I think I did it once. Hmm. Not sure ...

Any hints greatly appreciated!

Cheers to all. 

Michael.

Michael.

---

### Post by stevebakerj on 2007-09-20
> **MichaelSM said:**
> 
Otherwise;

VBOX I cannot  make the XP window fill the screen ( I have a 22-inch lcd). Not a major issue.

OK. The mouse pointer only works in the VBox window. There is an option for 'Control/Right' which should enable the  mouse pointer to move outside the VBOX parameters. I think I did it once. Hmm. Not sure ...

Any hints greatly appreciated!

Cheers to all. 

Michael.

Michael.

To resolve screen size and seemless mouse crossover just install 'Guest Additions'

With XP running in VBox goto:
Devices
Install Guest Additions

---

### Post by MichaelSM on 2007-09-21
Thanks again everyone for your assistance! I've been fiddling with VBox and I reckon it's amazing.

Only one small issue. Sorry.

I have a Brother MFC-3240C printer etc. I've run the install cd a few times (yes I have installed SP2) but the result is the same, as in everything BUT the PRINTING facility is not enabled when I look at Control Panel>Printers. AS in PC-Fax, Four Brother options available, but not hard printing.

Having installed Brother USB printers before, I know that it's imperative to NOT have the printer connected when running the install. Eventually a box pops up which says to connect the USB cable and power up the printer. 

At this stage, and following the instructions to connect the cables, and having done so, the install seizes up and won't complete. I've given it ten minutes but no further action. The 'Next" button never illuminates.

No rush, but any help appreciated.

Cheers.

Mike.

PS. It''s f$#@*n weird to be asking advice about Windoze on a Linux Forum. Just playing with it brings back nightmares......

---

### Post by MichaelSM on 2007-09-21
Hi again.

In case anyone is interested, I've got the MFC3240C installed and it printed a test page. I didn't use the proprietary disc.

Assuming a printer is installed and working on the 'host' OS; when one starts VBox, there is a set of options on the right highlighted in blue. Scrolling down, one of them is USB. Click on it, and a new window will appear. On the far right is vertical series of fuzzy icons. Clicking on the second one down should bring up a list of the USB gadgets connected to your host OS. I just added all of them.

Cheers. 

Mike.

---

### Post by asmoore82 on 2007-09-21
I don't think the virtualbox users group was created during install;
But I sidestepped the whole issue and I really like my solution...

:KS

[http://ubuntuforums.org/showpost.php?p=3372955&postcount=5](http://ubuntuforums.org/showpost.php?p=3372955&postcount=5)

[http://ubuntuforums.org/showpost.php?p=3388529&postcount=15](http://ubuntuforums.org/showpost.php?p=3388529&postcount=15)

EDIT: very late to post... but I compiled OSE from source so really don't think
my systems has/needs the vbox users group; it's good to know that using
the .deb package is straightforward after a login/logout though.

---

### Post by MichaelSM on 2007-10-05
Hello asmoore.

Since I'm using the 'other' (puel?) version of VBox, maybe those commands aren't for me.

I'm supposing you have set it up so VBox runs from boot, so's you don't have to hassle. arcing it up later, with all the acceptances of mouse command switches, etc.

I'd like to do that one day ....just to save a bit of time occasionally, but I don't use W very much.

I only installed VBox for one accounting program, and also for fun.

AutoCad also is perfect in VBox/XP, far better than Wine, of course.....

Seamless mode is sorta nice, but I find it easier to run VBox/XP in one workspace and Ubuntu in the other. Just have to remember to shut down VBox/XP before I shut down the computer. 

Thanks for your help.

Mike.

PS. In case someone else new to VBox reads this, I increased my RAM to 1.5 g. That made a big difference.

---

### Post by Ptero-4 on 2007-10-13
Hi. I installed kubuntu feisty on virtualbox on a winxp computer at a friends house and installed the "guest additions", but now the pointer won't show. Is there any way to fix it?

---

### Post by elgalloloco on 2007-10-28
> **raijinsetsu said:**
> ```
gpasswd -a michael vboxusers
```

Thanx 4 this!

---

