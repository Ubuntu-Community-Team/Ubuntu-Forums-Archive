---
title: "Laptop Install &amp; 5 Questions"
date: 2005-05-23
forum: Absolute Beginner Talk
---

### Post by kepardue on 2005-05-23
Hello all,

I'm going to be getting a laptop in the next few days and would very much like to try dual booting Ubuntu/Windows on it.  I'm confident I can get it installed, but beyond that I have several questions.  One of the things that I love about Ubuntu is the philosphy of getting things to "just work".  I don't have much experience (or success) with command line, or necessarily Linux for that matter, so bear with me.

1. Is there some way to have my account remember my 'admin' or 'sudo' password after the first time I enter it?  I mean, it's the same password as my main user account, so if someone can get into my system they can get into the admin section.  It's just a hassle to have to continually type that password in when I'm trying to synaptec something in, or get slapped with improper permissions trying to edit a file in a protected directory.

2. Related to #1, the only way I've found to edit a file such as the repository lists is to go in and do a sudo gedit from command line.  Is there a way that I can give myslef access to these files without going to the command line?

3. I do a little bit of web design / PHP for the company that I work for.  I've installed Bluefish, but how do I go about doing FTP.  The bluefish site seems to read that you have to use gnome vfs to do it.  So, I go to Places/Connect to server, type in the ftp:// address of my server and a username.  It prompts me for a password and asks to put it on a keyring (this is stupid--I have to enter a password to have the  thing remember a password?--again, is there any way to consolidate all of this?).  I can connect to the server okay, I can open the file in bluefish from the FTP server, but when I try to save it back to the server I get a write error.  Is there a way to manage this more like Dreamweaver does?  Having  a local copy and a remote copy of my files, to where I can just hit upload on whatever file I'm on and it's uploaded to the appropriate location on the server?

4. My company allows us to VPN in to have access to our Exchange server.  Is there an easy way to VPN into a network via Ubuntu?

5. Is there any similar alternative to Adobe's Photoshop Album Organizer to viewing photos?  I absolutely love it.  The main features that I'm looking for are tagging and viewing by date.  I'd like to have tags for Family, Friends, Places, etc. with options for subcategories.  That's a biggie.

---

### Post by Zelut on 2005-05-23
Let me see if I can answer your questions...

In regards to question #1 regarding remembering the root password there is a solution, yes.  If you're in the terminal (command prompt) and want to run a number of root commands you can type sudo -s, enter the password & you are then officially root until you exit.  

Please note however that running as root is generally not a good idea.  The reason that the password prompts are in place are not only for security from attackers but security from yourself.  Any linux vet would tell you its never a good idea to stay logged in as root.  You usually end up causing more problems than not.  The password prompt can act as a reminder.  Hopefully you know what you're doing after that point.

In regards to question #2 you can edit your repository files without using the terminal.  I think the terminal was suggested because it may be quicker.  If you'd like to do it thru your 'file manager' you can look for the same path & open the sources.list file thru double click (/etc/apt/sources.list is generally the path I believe)

for FTP work I suggest using gFTP.  you can use the command 'sudo apt-get install gftp' for that to be automatically installed.  Its really similar to SmartFTP that I always used under windows.

As far as VPN you can try the terminal based program ssh (# ssh domain.com) to browse that way.  As far as a GUI version I'm not sure, I use the terminal)

...and your last question I don't have an answer to.  I haven't looked for a album organizer comparable to photoshop's.  I'm sure someone else may have a suggestion.

I hope the rest of this helped or gave you some ideas..

---

### Post by poofyhairguy on 2005-05-24
[QUOTE=kepardue]
1. Is there some way to have my account remember my 'admin' or 'sudo' password after the first time I enter it?  I mean, it's the same password as my main user account, so if someone can get into my system they can get into the admin section.  It's just a hassle to have to continually type that password in when I'm trying to synaptec something in, or get slapped with improper permissions trying to edit a file in a protected directory.

2. Related to #1, the only way I've found to edit a file such as the repository lists is to go in and do a sudo gedit from command line.  Is there a way that I can give myself access to these files without going to the command line?[/QUOTE]


Well, you could create and admin account and run as that all the time, Windows style. Its not like that by default because that particular aspect of Windows is the reason for many of its security problems. Until Linux gets a virus, you would probably be safe though. But maybe not. I don't know, smarter nerds than me say its a bad habit to get into (it certainly is in Windowsland).

[QUOTE=kepardue]3. I do a little bit of web design / PHP for the company that I work for.  I've installed Bluefish, but how do I go about doing FTP.  The bluefish site seems to read that you have to use gnome vfs to do it.  So, I go to Places/Connect to server, type in the ftp:// address of my server and a username.  It prompts me for a password and asks to put it on a keyring (this is stupid--I have to enter a password to have the  thing remember a password?--again, is there any way to consolidate all of this?).  I can connect to the server okay, I can open the file in bluefish from the FTP server, but when I try to save it back to the server I get a write error.  Is there a way to manage this more like Dreamweaver does?  Having  a local copy and a remote copy of my files, to where I can just hit upload on whatever file I'm on and it's uploaded to the appropriate location on the server?[/QUOTE]

All I can say is...have you tried NVU?

[http://www.nvu.com/](http://www.nvu.com/)

If that doesn't work than you might have to do it by hand with an FTP program.

[QUOTE=kepardue]4. My company allows us to VPN in to have access to our Exchange server.  Is there an easy way to VPN into a network via Ubuntu?[/QUOTE]

This maybe?

[https://sourceforge.net/projects/gvpn-dialer/](https://sourceforge.net/projects/gvpn-dialer/)

Never tried it personally.

[QUOTE=kepardue]5. Is there any similar alternative to Adobe's Photoshop Album Organizer to viewing photos?  I absolutely love it.  The main features that I'm looking for are tagging and viewing by date.  I'd like to have tags for Family, Friends, Places, etc. with options for subcategories.  That's a biggie.[/QUOTE]

There is a new, exciting MONO app that does this:

[http://www.gnome.org/projects/f-spot/](http://www.gnome.org/projects/f-spot/)

I would check to see if its in the main Ubuntu repo, but I'm not at my box right now.

---

### Post by Gustav on 2005-05-24
[QUOTE=kepardue]
2. Related to #1, the only way I've found to edit a file such as the repository lists is to go in and do a sudo gedit from command line.  Is there a way that I can give myslef access to these files without going to the command line?[/QUOTE]
You can add a script in nautilus, do like this:

navigate to ~/.gnome2/nautilus-scripts/

make a file called "Open as root" or something like that

edit the file and write

```
#!/bin/bash
#

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "gnome-open $uri" &
done
```
save the file

Now you can right-click on files in nautilus and click on scripts->Open as root to open the file with root privileges.

---

### Post by kepardue on 2005-06-06
Well, I'm afraid I still don't quite see the point of making me re-log in to change some settings that I don't have to log in to fix on Windows.  Besides, for logging in as sudo to be extremely dangerous to be tempted only by power users who know what they're using, and only on brave occasions, there sure is a whole lot that requires me to log in to change.  What I don't understand is that the password that logs me in as the sudo is the same password that I signed up with on setup, so I sure as heck better know it.

I'm not meaning any negativity, but I'm afraid for right now it just requires too much time configuring (which means I spend less time working) to get Ubuntu/Linux to do what I need it to do.  I can't even set up my ATI Mobility Radeon 3D acceleration without reading that "this is not for faint of heart" warnings and screwing up my system to where I have to reinstall Ubuntu.  Linux really needs to get to the point where I can pop over to ATI's site (or better yet, have Ubuntu say, "hey, you've got an ATI!") and download a single file, to which I promptly double click and my video card drivers/3D acceleration is installed.... or be able to pop over to BBC News or CNN or ZDNet and watch the video headlines (whether it's Real or Windows Media)... or even be able to boot without watching the cryptic description of what's going on pass before my eyes like Matrix code... or have a browser with a default bookmark to something as obscene as "the urban dictionary"... or, well, do a number of things that the convenience of Windows allows me to do, or at least allows me to do without typing in "SDKLf /xc/a dfkds fsd;fl -s -ld//f- cxz- nvxcvj sdkfj s- sdafs" into a terminal to achieve.

I really did try, but I find myself hanging out in Windows more and more often.  There's just too much that just works there.  Ubuntu is the best step in the right direction I've seen to date.  It's the easiest to use thus far, and Gnome is fantastic with its less complicated desktop, configuration, and menu layout.  I did submit my laptop's hardware specifications to Ubuntu's database.  Here's to hoping that there will be greater multimedia focus, and a greater focus on separating the user from the configuration in Breezy.

Thanks, and I truly do apologize for my frustration.  I do realize that this is a free product and I should expect free quality and support out of it, and shouldn't complain terribly much about it.

Kenneth

---

