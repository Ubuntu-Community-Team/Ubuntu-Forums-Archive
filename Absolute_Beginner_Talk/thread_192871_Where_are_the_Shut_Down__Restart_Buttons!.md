---
title: "Where are the Shut Down / Restart Buttons?!?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by Luke771 on 2006-06-09
I upgraded from Breezy to Dapper, and now when I hit "Quit" in the start menu I don't see any "shut down" or "restart" option.

Why?!?

When I click "Quit" I get four choiches:

- Log out, which will take me back to the to the login screen
- Lock screen, which will lock the screen (duh)
- Switch user, well, OK, to switch user
- Hibernate, which will shut down the computer, but it won't start properly next time andI'll have to hit reset.

 Each time I want to shut down or restart I must run "Hibernate", then restart manually, then the boot process will fail (blank screen) and I'll have to hit the reset button on the box, then the boot sequence will want to check the file system because / was not cleanly unmounted, then I'll have to reboot again, and only then the computer will start.

Where are the regular "Shut down" and "Restart" buttons? 
I guess I have some wrong settings but I can't figure out where.

---

### Post by mostwanted on 2006-06-09
Are you running an x session you started with the startx command?

---

### Post by Luke771 on 2006-06-09
No, I'm running the X session that automatically starts after the default graphical interface login.

I have the same problem both logging in as regular user and as root: No Restart/ Shut Down options in the Quit dialog.

I had root logging enabled since before the upgrade but I had to enable it again after upgrading; I usually log in as root because I skip being asked for password all the time and I have write access to all drives and partitions (I'm aware of the risks)

---

### Post by popkid on 2006-06-09
if you run gconf-editor from the command line, there should be entries under apps, gnome power manager, for "allow suspend", "allow hibernate" etc, if you check the boxes, then you should get the options in the logout window, you will need to do this as user and as root I believe, as these are per-user settings

Hope this helps,

pK

---

### Post by Luke771 on 2006-06-09
Didn't work, thanks anyway.
All the boxes "allow hibernate" and stuff like that were already checked. I also tried editign, adding keys trying to figure out the syntax by looking at the existing keys and the info lines that are visibe when highlighting stuff in gconf-editor, but I couldn't get any Shutdown and restart buttons ion my Log Out dialog.

Anyone has more suggestions?
I'm still stuck with the no shutdown/restart buttons problem.

---

### Post by taurus on 2006-06-09
Actually, do you see a red icon on upper right corner???  You can do all that by clicking it...

---

### Post by hanexar on 2006-06-09
I don't know for your buttons, but next time you want to shutdown go in console mode (alt-ctrl+F1), login and do:

To shudown
```
sudo shutdown now
```

To reboot
```
sudo shutdown -r now
```

Maybe you could check if this work.

---

### Post by angkor on 2006-06-09
I had the same problem when I started a gnome session with kdm instead of gdm. Do you have kde installed as well? Or does this problem occur with gdm?

---

### Post by uzi09 on 2006-06-09
[QUOTE=hanexar]I don't know for your buttons, but next time you want to shutdown go in console mode (alt-ctrl+F1), login and do:

To shudown
```
sudo shutdown now
```

To reboot
```
sudo shutdown -r now
```

Maybe you could check if this work.[/QUOTE]

yeah, i used to use this before, then i learned about:
```

sudo halt

```
to shutdown and
```

sudo reboot

```
to reboot! a lil faster :D

ps: i'm having a similar trouble. the problem with mines is that i don't even get an option to do anything -- it just automatically logs me out :(
i posted a thread about this before, but didn't get much response. the closest thing to the solution that was given was perhaps that there was a bug in my theme that didn't allow me to use it.
i'm still stuck here unfortunately, and am still trying to figure out what that app is called when you click the logout/quit button and see if i can reconfig the shortcuts or something to launch that. any help would be greatly appreciated!

uzi

---

### Post by lapsey on 2006-06-09
for some reason hitting the power button on the case doesn't work in dapper (it did in breezy).

I miss that

---

### Post by Dr. Nick on 2006-06-09
some of them problesm sound like the gdm/kdm things discussed before. If you have both kde and gnome installed then you will run into this problem if you use kdm to start a gnome session or gdm to start a kde session.

---

### Post by Luke771 on 2006-06-10
No red buttons on Upper Right.
Sthutting down or rebooting in terminal is actually a cool suggestion, I never tried that as I thought that you had to end the X session and run the command in text mode. I guess I can shut down and restart from terminal then, thanks for the hint.

BUT

You "should" have Shut Down and Restart buttons in the graphical interface as well, right? So I guess the pronlem now is no longer "how do I shut down cleanly" but "why I don't have those buttons anyway"

I don't have KDE but I do have Enlightment installed because I wanted to try it out, but I use mostly Gnome. I could try and uninstall Enlightment and check out if the problem goes; in the meantime, if anyone has more possible solutions please post.

-thanks for the answers anyone.

The auto log out is controlled by the "ask on logout" option (I think it's under "sessions")
Hitting the button on the case can be configured to shut down or reboot in gconf-editor

---

### Post by jdusablon on 2006-06-10
I agree 100% with that. It only happened to me when I made an XGL session and decided to start using it by default when it proved itself to be stable.

Now I only have Hibernate, no Restart, no Shutdown.

I looked for gconf-editor -> apps -> gnome-power-manager -> "allow suspend", "allow hibernate" Didn't find them as root or as self.

Because I can still use my original, regular-old xorg session and find these buttons, I suspect there's something to flag in the session configuration.

---

### Post by Dr. Nick on 2006-06-10
[quote=jdusablon]I agree 100% with that. It only happened to me when I made an XGL session and decided to start using it by default when it proved itself to be stable.

Now I only have Hibernate, no Restart, no Shutdown.

I looked for gconf-editor -> apps -> gnome-power-manager -> "allow suspend", "allow hibernate" Didn't find them as root or as self.

Because I can still use my original, regular-old xorg session and find these buttons, I suspect there's something to flag in the session configuration.[/quote]

How did you do xgl? I used my sig link and still have all shutdown/restart options in a gui. I modified the ending though and just added "thefuture" to the session startup programs.


oh and the enlightnement poster, are you using gdm or the enlightnement login manager? If gdm then shutdown/restart should work out of gnome

---

### Post by oskie on 2006-06-10
I am having the same problem. I believe it happened just after I installed a Gnome theme by simply taking the compressed file and popping it in the theme manager (perhaps I should have uncompressed it first?). I have not been able to get the buttons back even after uninstalling the theme. Very frustrating as I particularly like the look of the shutdown prompt in Ubuntu.

---

### Post by Luke771 on 2006-06-10
Well I guess it's a bug then.
Someone should report it. I never used BigZilla, someone who alredy can use it please do that , thx.

In the meantime, I'm using these commands in a terminal window (no need to end the X session):```
root@ubuntu:~#reboot
``` and ```
root@ubuntu:~#halt
```

Which of course turns in ```
user@ubuntu:~$sudo reboot
``` and ```
user@ubuntu:~$sudo halt
``` If you are not logged in as root 

I guess that will do the trick while waiting for the bug fix.

---

### Post by jdusablon on 2006-06-11
Dr. Nick: I used [this]("http://www.ubuntuforums.org/showthread.php?t=168618") guide for ATI/Gnome.

It sets up a whole separate XGL session, which is supremely necessary for proper troubleshooting, IMO. Much less intrusive install.

Now that I'm using that session permanently, I need to solve this.

---

### Post by Lfrb on 2006-06-11
Same thing for me..

I have a session for XGL and when I log in with this session.. I no more have the Shut Down / Restart icons :( 

Very annoying :confused: 

--
Louis-Francis

---

### Post by hanexar on 2006-06-11
Just a though...  Have you tried reinstall the gnome panel / menu / session package?  It might bring the buttons back...

By the way, thanx for the shorter command for shutdown and reboot ;)

---

### Post by jpneal on 2006-06-11
I also had this problem, and have solved it by uninstalling kdm using Synaptic.

---

### Post by Dr. Nick on 2006-06-11
Every one having this problem try this first. Its simple but could be overlooked,

Right click a panel, hit add to panel, then add the quit button and see what happens.

About the xgl. I really dont remember the specifics of my install but I have xgl/compiz working per the tutorial in my thread and the shutdown/logoff is working aswell.

I didnt really make a seperaete xsession for mine if I recall, just set xgl to start on boot form the system- prefrences- sessions dialog by adding the script "thefuture" to startup programs

---

### Post by uzi09 on 2006-06-15
@Dr.Nick
yah, so that didn't work... :D

hmmm, this is really odd. i am very surprised that no one knows how these applets/menus work. like does it initiate a script? or is it just a command it runs? is it possible to modify this in any way (without recompling the kernel pls :P)?

any help is much appreciated...

---

### Post by Dr. Nick on 2006-06-15
Well I though I posted a "fix" in this thread but apparently it was another

Let me preface this by saying it is just a workaround, Since I am not having this problem I cant really troubleshoot it. This workaround basicaly involves making a script to shutdown the computer, or reboot it

Create a new text document and name it either shutdown or restart depending on what you want to do.

This specifically only works in gnome, KDE would be the same principle but gksudo would change

Add the following code to the text file to shutdown, save the file somewhere you have access to.


```
#/bin/sh
gksudo halt
``` 
And make one like this to reboot


```
#/bin/sh
gksudo reboot
``` 
Save both these files to your hard drive, then right click them and hit

Properties - Permission - and set the owner to execute them

Clicking them should ask what you want to do, click run to execute it. 

To make things a bit easie,r in gnome drag and drop the files to the toolbar to create a launcher,  you can set up nice icons for them and restore alot of the missing functionality.

I understand this is only a workaround, but it helps in the mean time until the problem is figured out and corrected.

---

### Post by manatlan on 2006-06-16
Same problem here ...
with XGL installed in a "gdm session" (method A of the official wiki)

now, i'd created a button in the panel ;-(

---

### Post by jdusablon on 2006-06-18
**Dr. Nick**, your solution is great and I appreciate your effort.

But the issue is that we'd like these buttons to simply work like they do in the normal xorg gnome session. I'm absolutely positive that it has something to do with the new session.

Sure, they say "Make this session my default," but there seems to be something not switched over...

I've been poking around in /usr/share/xsessions and other places...still can't find anything... I have a feeling it has to do with killing the gnome session and starting a new one.

---

### Post by Protazoid on 2006-06-18
Hey guys I had this same problem when changing the theme of my login manager by selecting a tar.gz package.

To fix it all I had to do was select  "Show action menu" in the login window preferences settings.  Its under the header "Menu Bar"  hopes this helps as it was such an easy fix :D.

Cheers Protazoid

---

### Post by uzi09 on 2006-06-18
that's for GDM (the login screen)!

nice try though :D

---

### Post by iluminate on 2006-06-20
> Hey guys I had this same problem when changing the theme of my login manager by selecting a tar.gz package.

To fix it all I had to do was select "Show action menu" in the login window preferences settings. Its under the header "Menu Bar" hopes this helps as it was such an easy fix .

Cheers Protazoid

I had the same problem, no reboot or shutdown button in Gnome but select "Show action menu" did the trick :) Gr8 and a big thank you. Spent hours to find where the prob was.....

Cheers to all

---

### Post by yugo on 2006-06-21
It doesn't work for me. "show action selected" was already selected

---

### Post by uzi09 on 2006-06-21
[QUOTE=iluminate]I had the same problem, no reboot or shutdown button in Gnome but select "Show action menu" did the trick :) Gr8 and a big thank you. Spent hours to find where the prob was.....

Cheers to all[/QUOTE]

isn't this under "Login Manager", IE: for GDM???

When you guys say you have no "shutdown restart buttons" are you talking about once you've logged in, or on the LOG IN SCREEN?!?!

---

### Post by jdusablon on 2006-06-22
After logged in, I have no Restart or Shutdown buttons. Once logged out & at the login prompt, I can restart, shutdown, etc.

---

### Post by mkaragia on 2006-06-22
Same problem here. After login, by clicking on the little door icon up-right on the screen I am presented with the familiar panel (which I also get by briefly pussing the Power button on my laptop) with the Hibernate option covering the whole bottom line, where used to be my Restart and Shutdown buttons. I am using Xgl and Compiz as well, so I start to suspect that this problem has something to do with the different session I manually added.

---

### Post by uzi09 on 2006-06-24
same issue with me 2.

one thing though, i noticed this occuring before i even installed xgl (aiglx actually) on my comp.
i did however change the theme. if there are any pro theme designers, do u know if there is a possibility for a theme to cause this??

man, i'm surprised so many people have this issue, yet no resolution. i have no idea how to work bug buddy, nor do i know how to recreate the issue. i wish we could just e-mail the devs on this :S

---

### Post by phoenixleo on 2006-06-25
Same problem here on a fresh Dapper install on an old Fujitsu-Siemens S-4546.

At login only options are to choose session and choose language.
Once logged in System -> Quit or top-right Quit button will give the same dialog as described in OP. As suggested earlier I checked out gnome-power-manager in gconf-editor, but found no relevant setting. I did find action_button_power, though, so at least I could change that from "hibernate" to "shutdown".

---

### Post by 3rdalbum on 2006-06-25
Same problem happens to me, but I think it only happens when I log in with XGL.

---

### Post by uzi09 on 2006-06-25
[QUOTE=phoenixleo]Once logged in System -> Quit or top-right Quit button will give the same dialog as described in OP. [/QUOTE]

see, this actually doesn't even come up for me. it just straight logs me out. i wonder if it's like some automated setting, because when i first used to have it, all i'd do is log out from it, and i guess it "realized" that and it just straight logs me out now :S.

problem with me is that there is no warning :(. i accidently hit that stupid button in the corner a couple of times, and lost everything ](*,) 

thanks to gmail's auto save feature, it saved me a couple of times :D
so right now, i just removed that button altogether, but ideally, i'd like to use it every once in a while.

---

### Post by jason.b.c on 2006-06-26
Is this problem only happening when people are upgrading from breezy to dapper or is this a Dapper install CD to hard drive problem as well...?????

Oh Man..!  Don't tell me i'm going to have to go through this crap too...](*,)

---

### Post by uzi09 on 2006-06-26
you bring up a good point.
i didn't upgrade from breezy, but i did install a few months early. perhaps they overlooked it and none of the updates seemed to clear up the issue.

i'm curious, has anyone tried to reinstall gnome to try to correct this issue? if so, can you please let us know if it corrected the issue??

thanks

---

### Post by uzi09 on 2006-06-26
wow, my computer just tripped out, sorry. please remove all but one of these posts!
thx

---

### Post by jason.b.c on 2006-06-26
[QUOTE=uzi09]wow, my computer just tripped out, sorry. please remove all but one of these posts!
thx[/QUOTE]


You fixed it..???  How.???;)

---

### Post by Dr. Nick on 2006-06-26
I would think the issue could be corrected just by undoing all the xgl stuff? 

Though I am running xgl and have 0 problems :confused:

I am curious to what causes all these problems, just cant look myself. Ill keep a eye out for any solutions

---

### Post by Dr. Nick on 2006-06-27
[quote=Dr. Nick]I would think the issue could be corrected just by undoing all the xgl stuff? 

Though I am running xgl and have 0 problems :confused:

I am curious to what causes all these problems, just cant look myself. Ill keep a eye out for any solutions[/quote] 
EDIT

Look here at post 27
[http://www.ubuntuforums.org/showthread.php?t=174233&page=3]("http://www.ubuntuforums.org/showthread.php?t=174233&page=3")

I did not follow that guide and mine works, anyone having this issue use the guide in my signature?

I modified the ending a bit to avoid editing my xsession file and I am happily on xgl and have all shutdown options

---

### Post by uzi09 on 2006-06-27
thank you dr.nick for those links.

i personally don't think it's quite an XGL issue (probably an issue with XGL **AS WELL**), because i had this problem before i even installed XGL.

---

### Post by GayRockies on 2006-06-27
I just installed ubuntu (Dapper Dan) on a machine last night, and I started having this issue as well.  The only thing I've done to the machine is to try to install Wine so that I can run one Windows app and make sure it works before migrating another maching to Linux.  This machine was running Windows XP this time yesterday morning, so I doubt that I did much to cause this button to go away.  The first time I shut the machine down in ubuntu, the button was there...  then it was not.

Thanks for the terminal shutdown commands...  that is sure better than shutting down a machine with the OS running (yikes!), but please, if anyone finds a solution to this, post it here!

I will make a quick comment that ubuntu was actually the second distribution I tried (Ark Linux was the first), and I came to ubuntu because of these forums, IRC, etc. support.  There's something to be said for finding better support (and I mean that) from free software than for massively overpriced software.

Kind regards,

M.J. in Colorado

---

### Post by uzi09 on 2006-06-27
interesting. i installed wine as well. hmm, i wonder if that did it.

anyone else install wine?

---

### Post by mkaragia on 2006-06-29
I am pretty certain I don't have wine installed. I am running XGL though as previously mentioned.

---

### Post by Luke771 on 2006-06-29
Must have been the muliple desktop environments: when the problem first showe up I had just upgraded from Breezy and installed the Enlightment X-Windows Manager.

Both my OSes were really getting messy (WinXP by installing/uninstalling games all the time, and Dapper because of ... same thing with network tools instead of games)

I have the OSes installed in relatively small partitions and I store data on dedicated file storage partition (running Ext2 with Win Ext2 drivers) I could run a clean install without having to run major backups.

So I re-installed both OSes from scratch, even deleting and re-creating their partitions: this time I installed Gnome *only* and I was very careful when adding programs from repositories not to choose anything requiring the KDE environment installed.

It worked: all the buttons show up and everything is working just fine. Only "strange" thing is, it seems to me that Dapper runs somewhat less smoothly than Breezy, but that may be caused by my outdated hardware (Duron 1600/512RAM)

The no-shutdown/restart-buttons problem has been solved by ceanly install everything, which is no real solution anyways, but it should be noticed that I did not get the same problem again, the only difference being the "strictly-Gnome-only" configuration.

I have Wine installed and it not causing any problem.

---

### Post by uzi09 on 2006-06-29
yet another good point. i too installed kde desktop on my breezy (other comp) and later i had the same issue w/ the restart/shutdown buttons.

this time, i only installed xfce DE on my dapper, and again, same issue. i guess any new DE installed will cause this -- even COMPIZ.

i'm going to go try a reinstall of ubuntu desktop and hope it helps.

EDIT:

k, so i tried to do:
```
 sudo aptitude reinstall ubuntu-desktop
```
but because i actually installed ubuntu (as opposed to kubuntu, or xubuntu), i apparently don't have the ubuntu-desktop package (or metapackage) installed.
i then just tried to install it like so:
```
sudo aptitude install ubuntu-desktop
```
but when i logged out and tried loggin back in (using Gnome for my session), it didn't do/look any different. the Quit didn't work either :S

is it possible to just reinstall that one part?
here's a pic (second one is the latest one):
[http://www.manucornet.net/ubuntu/#logout_dialog](http://www.manucornet.net/ubuntu/#logout_dialog)

any help is much appreciated!

---

### Post by MentePC on 2006-07-01
Gee, I have this same problem too.

I installed Xgl in such a way that I may login using the gnome session or gnome-xgl session (no invasive installation).

If I log-in with the Gnome session, everything works fine. If I log-in with the Gnome-xgl session I do not have the Shutdown or Restart buttons in the Quit Screen (accesible clicking on the red icon near the clock), just the Hibernate button taking the whole bottom line.

Notice that I do not need to have Compiz running for this problem to happen, just plain XGL.

I have also another issue, I cannot create a new user now and use the Gnome-XGL on the new account because the session fails to start and is log-out in less than 10 seconds. On the error message, it says "cannot create /tmp/.X1-lock". I've tried deleting this file but then the error message changes  to "already existing X server".

I've started using Ubuntu Dapper Drake for 2 days, I'm fairly new to Linux, and I have already followed tons of tutorials and edited hundred of config files, not knowing exactly what they are for (I still do not know the difference between display:=1 and display:=0).

I'm using Linux alone here because I cannot create user accounts for my family, and they got interested on Linux just because of XGL+Compiz and making them use the normal X server will simply make them go back to Windows.

Does anybody knows how to fix these 2 issues ?
(no shutdown/restart button under XGL, error while loggin-in as another user)with XGL).

I found these sites, but they didn't help much:

[https://launchpad.net/distros/ubuntu/+source/gnome-panel/+bug/36321](https://launchpad.net/distros/ubuntu/+source/gnome-panel/+bug/36321)
[https://launchpad.net/distros/ubuntu/+source/gnome-session/+bug/44585](https://launchpad.net/distros/ubuntu/+source/gnome-session/+bug/44585)

---

### Post by mike4ubuntu on 2006-07-07
Does anybody know what the command-line command is for popping up the "log off, switch user, lock screen..." dialog is?  In other words, what is the little red gnome panel button bound to?

---

### Post by verteidi on 2006-07-08
I found another workaround for this problem using the power-off button on my laptop (it usually made the shutdown menu appear). Don't know if this works on other machines as well:
Open a terminal and run
```
gconf-editor
```
Go to apps --> gnome-power-manager and find the entry "action_button_power". Change "interactive" to "shutdown".
Your computer should now automatically switch off when you hit the power-off button. This will probably work with "restart" as well.

---

### Post by mech7 on 2006-07-11
I have this too only when logging in with XGL session :(

---

### Post by adam.tropics on 2006-07-11
The options dissappear if you installed an xgl sessionm rather than editing /etc/gdm/gdm.conf-custom. So you have the choice of safer session control and losing these options, or much slower start and keep these options. Almost. The issue really seems to be the ability to restart and shutdown by hitting a  button without entering a password. Make your own....[here!]("http://www.ubuntuforums.org/showpost.php?p=1043773&postcount=4")

---

### Post by rectangle on 2006-07-11
> **mech7 said:**
> I have this too only when logging in with XGL session :(
Yes, same here but I dont find it much of a problem. I just log out and use the Options in the lower left corner of the log in screen to shutdown or restart.

---

### Post by budhaboy on 2006-07-11
I just solved this very same problem:

go to: system->administration->login window

Then ensure the menubar, 'show actions' box is checked as well as the 'include hwstname...' box is checked.

This seemed to fix the problem.

I have no idea why.

---

### Post by bsndabmb on 2006-07-11
Hey thanks, budhaboy that worked great! Now I have my shutdown and restart buttons back!

---

### Post by rectangle on 2006-07-11
> **budhaboy said:**
> I just solved this very same problem:

go to: system->administration->login window

Then ensure the menubar, 'show actions' box is checked as well as the 'include hwstname...' box is checked.

This seemed to fix the problem.

I have no idea why.
Doesn't work for me. Both these boxes were already ticked:(

---

### Post by adam.tropics on 2006-07-12
> **rectangle said:**
> Doesn't work for me. Both these boxes were already ticked:(

Yeah, it seems to me people are getting a little confused. The login screen options affect the, well, login (therefore also the login screen you see when you logout). I was under the impression the thread was targetting the...

---

### Post by budhaboy on 2006-07-12
> **adam.tropics said:**
> Yeah, it seems to me people are getting a little confused. The login screen options affect the, well, login (therefore also the login screen you see when you logout). I was under the impression the thread was targetting the...

I got nothing, brother... My 'logout' window looked EXACTLY like yours, then I fiddled with those buttons, and now it looks the way it used to.

---

### Post by budhaboy on 2006-07-12
> **rectangle said:**
> Doesn't work for me. Both these boxes were already ticked:(

Sorry about that... it must be a different issue then, and somehow I managed to fix it without having any idea why. My logout box used to look like the one in the screen capture below. I fiddled with those boxes, and now it's got the 'reboot' and 'shutdown' buttons.

---

### Post by uzi09 on 2006-07-14
k, so started to google and came across [this](http://mail.gnome.org/archives/gnome-list/2004-December/msg00085.html) thread.

i was having the same, exact problem, only thing is that i don't have a "Desktop Preferences" under Applications menu.


EDIT: idk if any of you have seen this thread, but it gives a solution for ati cards:
[http://www.ubuntuforums.org/showthread.php?t=157923&page=2](http://www.ubuntuforums.org/showthread.php?t=157923&page=2)

---

### Post by MikeBenza on 2006-07-16
I have the no-shutdown-or-restart problem too...I had GNOME and KDE installed.  Since I don't use KDE, I uninstalled it.

Both before and after the uninstall, I tried going to System -> Admin -> Login Window.  It asked for my password, I got the mouse cursor to say that it's doing something, and then nothing happens.  The Login Window window does not open.  Any advice?

- Mike

---

### Post by adam.tropics on 2006-07-17
> **MikeBenza said:**
> I have the no-shutdown-or-restart problem too...I had GNOME and KDE installed.  Since I don't use KDE, I uninstalled it.

Both before and after the uninstall, I tried going to System -> Admin -> Login Window.  It asked for my password, I got the mouse cursor to say that it's doing something, and then nothing happens.  The Login Window window does not open.  Any advice?

- Mike

Yeah sure! Try running it from terminal, and see what the errors are, so from terminal,

```
sudo gdmsetup
```

and post any errors.

---

### Post by MikeBenza on 2006-07-18
> **adam.tropics said:**
> Yeah sure! Try running it from terminal, and see what the errors are, so from terminal,

```
sudo gdmsetup
``` 
and post any errors.
```

mike@ubuntu:~$ sudo gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.

``` 

I checked the man page for gdmsetup, and the conf file is in the right spot (/etc/gdm/X11/gdm.conf and the alternative place, /etc/gdm/gdm.conf) and world readable.  

I tried reinstalling ubuntu-desktop, but that didn't do anything.

I searched around for this problem.  It seems other people had this problem, but none posted their solutions, or their problem was caused by something that is fine on my machine (i.e. enough disk space).[]("http://www.ubuntuforums.org/showthread.php?t=190821")

---

### Post by adam.tropics on 2006-07-18
I hate to say it Mike Benza, but the best I can suggest is starting another thread for this problem, or maybe reviving one of the previous threads on this topic, as I have not come across this one myself, although you're right in that others seem to have done! Sorry!

---

### Post by uzi09 on 2006-07-18
not to sure what the problem is there, but in general, you should use gksudo for graphical apps vs sudo.

[click here for more info](http://psychocats.net/ubuntu/graphicalsudo.php)

EDIT: k, so i think we all have realized that there's like 2 *slightly* different problems people have been looking at in this thread.

1)no "shutdown/restart" buttons when in a XGL/Compiz session

2)no shutdown/restart/logout/lock/suspended/etc dialogue box appearing at all when you hit the Quit button. (this is the one i was having)

i didn't realize it at first that we were talking about 2 different things. anyways, for anyone else who is having the same problem as me (or whoever comes across this thread through google) i figured out the answer (for (2)).

in Gnome 2.14.2, you have to go to:
System > Preferences > Sessions
and make sure "Ask on Logout" under the "Session Options" tab is checked.

i've been searchin for this answer for so long, and didn't realize it was as simple as that ](*,)

---

### Post by Jhongy on 2006-07-19
@uzi09: Does this fix the first or the second issue???

---

### Post by adam.tropics on 2006-07-20
I believe that fixes the second. But to clarify the first, I don't believe it's compiz that's the problem, I am pretty sure it's actually the xgl that's the problem. Will check that out.

---

### Post by adam.tropics on 2006-07-20
It's definitely xgl, as there is no restart with or without compiz.

---

### Post by Jhongy on 2006-07-20
I understand what the *problem* is... or at least, I think I do (still a newbie).... When installing XGL, I created a new desktop session, and then set it as default... if I were still using the default gdm session, I assume this wouldn't be a problem.

For reference, I installed XGL using the instructions here: [http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189).

So, the question becomes: How do we fix this?

---

### Post by adam.tropics on 2006-07-20
I hate to say it, but with the xgl issue, I believe it's a bug still waiting to be fixed. You can make single click restart/shutdown panel buttons though as a [temp workaround.]("http://www.ubuntuforums.org/showpost.php?p=1043773&postcount=4")

---

### Post by uzi09 on 2006-07-20
sorry for the confusion. i edited my post to clearify this.

i was actually talking about the second issue.

because this has been such a big issue, i've continued to look for a solution. here's something i came across...
----------------------------------------------------

 Method 2 - New GDM entry starts GNOME with XGL

Note: this method starts an XGL session seperate from GDM (GDM starts on a regular X server), which means GDM doesn't actually manage the session - causing several issues. The first method is more proper.

Simple (UTjunkie) method which seems to work. The only problem I've found with this method is that you can no longer directly shut down or restart from GNOME. You have to first log out and then choose the shut down/restart from GDM. I'm going to do this for GNOME with Nvidia, but it's basically the same for other settings...:

As root: create /etc/X11/sessions/gnome-xgl.desktop using your favorite text editor (mine's nano.....so laugh at me) It's contents should be:
```

[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=startxgl-custom
TryExec=startxgl-custom
Name=GNOME with XGL support
Name[en_CA]=GNOME with XGL support
Name[en_GB]=GNOME with XGL support

```
Now create /usr/bin/startxgl-custom. Put this in it:
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer & # This is for ATI users, NVIdia users should use: Xgl :1 -ac -accel glx:pbuffer -accel xv
DISPLAY=:1 gnome-session

```
And make it executable:
```

chmod 755 /usr/bin/startxgl-custom

```
Next let's create /usr/bin/compizrc. It's contents should be:
```

#!/bin/bash
DISPLAY=:1 LD_LIBRARY_PATH=/opt/mesa-xgl-cvs/lib/ compiz --replace gconf &
DISPLAY=:1 gnome-window-decorator & 

```
Make it executable too:
```

chmod 755 /usr/bin/compizrc

```
Now in GNOME go to Desktop>Preferences>Sessions. The go to the "Startup programs" tab, click Add and type "compizrc". Click OK adn the Close. And you're done. You now have an additional entry in the "choose session" under GDM. You have the option of loading up gdm with or without xgl from within GDM. If you're using different hardware, or want to add other desktop environments, edit /usr/bin/startxgl and replace the "gnome-session" with your favorite desktop environment Obviously you can create more of these .desktop files in the /etc/X11/sessions directory for other configurations or window managers.

Please note that I chose my locale. If you're living somewhere else, you'll probably want to choose yours. You can get a full list of the locales (and copy and paste the text into your new .desktop file) from any of the files that were originally in /etc/X11/sessions/. If you get the locales wrong, the name will come up in GDM as "foo" or something, not the description you gave it. 

source: [http://wiki.archlinux.org/index.php/Xgl](http://wiki.archlinux.org/index.php/Xgl)
------------------------------------------------------------------

so perhaps it only happens if you set it up as a seperate session. one suggestion for those of you who'd like it this way, you can easily remove compiz from startup. i'm not booted into linux right now, but i'll be sure to get back to you with a way. this way, you can start it up as you please.

---

### Post by jdusablon on 2006-07-20
I made a new [thread]("http://ubuntuforums.org/showthread.php?p=1279704#post1279704") for this problem.

(EDIT) **uzi09**, thanks for the research, but that is basically the "separate session" method of setting up XGL/Compiz. It doesn't solve the button problem.

> The only problem I've found with this method is that you can no longer directly shut down or restart from GNOME.

---

### Post by uzi09 on 2006-07-20
no, i know that, that's why i said:
[quote=uzi09]
so perhaps it only happens if you set it up as a seperate session. one suggestion for those of you who'd like it this way, you can easily remove compiz from startup. i'm not booted into linux right now, but i'll be sure to get back to you with a way. this way, you can start it up as you please.
[/quote]

---

### Post by macogw on 2006-07-20
> **mkaragia said:**
> Same problem here. After login, by clicking on the little door icon up-right on the screen I am presented with the familiar panel (which I also get by briefly pussing the Power button on my laptop) with the Hibernate option covering the whole bottom line, where used to be my Restart and Shutdown buttons. I am using Xgl and Compiz as well, so I start to suspect that this problem has something to do with the different session I manually added.
That's how mine is.  I did not go Breezy -> Dapper.  I did not install KDE.  I spent yesterday unzipping the source into /usr/src/linux and installing build-essential.  That's all I did to it.  Today, I have no shut down or restart (but I read this thread yesterday and knew what to type in command line).  I also didn't have sound yesterday or today.  I had to shut it down and turn it back on (regular restart didn't do it).  The only other thing I did was try to install a driver as an external module which, uh, didn't work because I don't have module.symvers (working on putting the patch for that in so it'll work again).

---

### Post by Jhongy on 2006-07-24
I reinstalled Compiz and XGL this weekend, according the the how-to posted on the Compiz.net forums.

This time, I didn't lose my shutdown or restart buttons.

---

### Post by lapsey on 2006-07-24
> **verteidi said:**
> I found another workaround for this problem using the power-off button on my laptop (it usually made the shutdown menu appear). Don't know if this works on other machines as well:
Open a terminal and run
```
gconf-editor
```
Go to apps --> gnome-power-manager and find the entry "action_button_power". Change "interactive" to "shutdown".
Your computer should now automatically switch off when you hit the power-off button. This will probably work with "restart" as well.

nicem, very nice ! :)

---

### Post by Dubbayoo on 2006-07-27
I have this problem and I don't use compiz at all. It comes and goes though. If the buttons are missing I can get them back by rebooting or sometimes just by ctrl/alt/backspace

---

### Post by infoseeker on 2006-07-29
Same problem here (only wide hibernate button on bottom row). I installed KDE from the Kubuntu 6.06 CD about a month ago.  I then later installed 'ubuntu-desktop' but Gnome was really weird after the installation (only a short white bar (panel) on top left, onto which I had to add applets, menu,.... everything!).
Today I am still using KDM and not GDM.  I have NOT as yet installed GLX at all. I have to return to KDE and reboot from there if required :(.

PS. I know the command line would do it (sudo reboot), quitting X, etc.  but what the hell...I use KDE 90% of the time anyway, so its not really an issue to me.

EDIT
Thought I would investigate this a bit further and did> sudo dpkg-reconfigure gdm to change from KDM to GDM and guess what....the buttons are all back to normal (restart has returned). I am going to re-enable KDM and see if they remain.

EDIT
Reverted back to using KDM and the Hibernate button is back to full width....no restart !  :confused:

---

### Post by exgsr on 2006-08-04
[SIZE="5"]**SOLVED!**[/SIZE]
i encountered this problem..
logged into dapper, click to download latest update.
then my **restart and shutdown button gone a.w.o.l!!**
In place where there use to be restart, hibernate and shutdown have been replace with one BIG hibernate button.

on the login screen also missing the "action" option for shutdown, restart, sleep etc.

i posted the solution to my problem in the other posting.
[http://www.ubuntuforums.org/showthread.php?p=1337190#post1337190](http://www.ubuntuforums.org/showthread.php?p=1337190#post1337190)

hope this will help those who faced the same problem ;)

---

### Post by LamB on 2006-08-04
> **Protazoid said:**
> Hey guys I had this same problem when changing the theme of my login manager by selecting a tar.gz package.

To fix it all I had to do was select  "Show action menu" in the login window preferences settings.  Its under the header "Menu Bar"  hopes this helps as it was such an easy fix :D.

Cheers Protazoid

thanks!! that solved the problem...

---

### Post by vayde on 2006-08-05
Doing the opposite didn't help me.

Pushing the red 'power' button yields:

Gnome Session: 4 options on lower row (suspend, hibernate, restart, shutdown)

Xgl Session: 2 options on lower row (suspend, hibernate)

---

### Post by dolphinsonar on 2006-09-19
Go throught these steps first, it might be this simple:

System > Administration > Login Window .... [x] Show Actions menu (check this)

[IMG]http://static.flickr.com/86/247725707_ac81551db9.jpg?v=0[/IMG]

---

### Post by macogw on 2006-09-20
```
sudo gedit /etc/gdm/gdm.conf-custom
```
Where it says:
SystemMenu=false
change it to:
SystemMenu=true
then restart

---

