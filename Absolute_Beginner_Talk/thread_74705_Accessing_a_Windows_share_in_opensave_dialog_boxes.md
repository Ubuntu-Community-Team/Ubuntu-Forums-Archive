---
title: "Accessing a Windows share in open/save dialog boxes"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by JazzCrazed on 2005-10-12
Hi all,

I've mounted a couple of shares via Places->Connect to Server, and they show up just fine on the desktop and in the Places menu.

In some instances I need to access these shares or save directly to them; however, I'm unable to locate them in a save/open dialog. Where would I find the shares after they've been mounted? I've searched, to no avail. I've also tried adding it to my fstab per [Ubuntu Guide's walkthrough]("http://ubuntuguide.org/#automountnetworkfoldersall"), to no avail - I get a wrong file system type error for smbfs.

Any help is much appreciated!

---

### Post by Kapre on 2005-10-12
> **JazzCrazed]Hi all,

I've mounted a couple of shares via Places->Connect to Server, and they show up just fine on the desktop and in the Places menu.

In some instances I need to access these shares or save directly to them said:**
> Ubuntu Guide's walkthrough[/URL], to no avail - I get a wrong file system type error for smbfs.

Any help is much appreciated!

jazzcrazed - are they NTFS? If they are, I dont think you can write to them yet. Sure they will mount and you can read them, but write to them (I think devs are still working on it) I doubt.

K

---

### Post by JazzCrazed on 2005-10-12
Thanks for your response, Kapre!

I'm sorry, I should have been more clear to start.

It is an NTFS share; however, I doubt seriously that I'm limited on writing to it, since I have mounted it in the Places menu and am able to copy files from, and most importantly, *to* it. I would guess that if I'm able to copy files to it that I am not restricted by the inability for non-Windows OS's to write directly to NTFS. It's a network share on a Windows 2000 Server - doesn't that make it SMBFS to clients connected to it?

Or am I totally off base? (Wouldn't be the first time...)

But whatever the case, I *am* able to copy files to it.

And also whatever the case, whether or not it's NTFS does not answer the issue of not being able to see it in open/save dialogs. I should at least be able to *navigate* to it, if only to get an error when I try to save anything to it. The way it is for me, they are nowhere to be seen in these dialogs, and can only be accessed via links that appear on the Desktop and in the Places menu.

Thanks again!

---

### Post by skirkpatrick on 2005-10-12
Yes, you are talking to it using Samba so it doesn't matter that it's NTFS.

Now for the other part, are you using Breezy or Hoary?  I'm not sure if this will work in Hoary but open your share from Places.  For example if you added a share called Public, it should appear on your Places menu between "Network Servers" and "Connect to Server...", just double-click on it to open it in Nautilus.  Now, in Nautilus, click on the Bookmarks menu then "Add Bookmark".  It should now show up in Places under your "Home Folder" and "Desktop" bookmarks.  It will now be accessible from your open file dialog from any application.

---

### Post by wylfing on 2005-10-12
That's a really good idea, skirkpatrick. I don't know for sure if it will work, but if it does that's great.

Another way to go is to directly open a location from the Load/Save dialog. When you're looking at (for example) an Open File dialog, hit Ctrl-L and an Open Location dialog will pop up. Type in the address of the SMB share in this form:

smb://servername/sharename

You can use Ctrl-L from most Nautilus windows.

---

### Post by JazzCrazed on 2005-10-12
Hi again skirkpatrick!

First off, I am using Breezy Badger 5.10, as well.

I've opened up the mounted shares from the Places menu and did as you said, choosing "Add Bookmark" from the Bookmarks menu. It now appears in the Places menu in the very top echelon - together with Home and Desktop. And it also shows up in every Nautilus window under the Bookmarks menu.

However, I'm still unable to find it in open/save dialogs...Although that seems dependent on the app.

Gedit, and now Writer, too, can both see the shares just fine. This may be because I had started both of these applications from files on the shares in the first place (by opening the file from Nautilus, rather than through their respective open dialogs). Inkscape is still a no go.

**wylfing**: I also tried out your trick; however, it likewise only works certain applications, such as Gedit (where the shares are viewable anyway in the left-side panel). Back in Inkscape, I get a "cannot open folder because it is not local" error. I also tried and failed similarly in Gaim (when looking for a file to send to a buddy).

I'm going to see if Inkscape still is stubborn about it when launched directly from a file on one of the shares...

Thanks again!

---

### Post by JazzCrazed on 2005-10-12
No go with opening straight from Nautilus... I created an SVG file in Inkscape which I saved to my Home folder.

I then copied it to one of my mounted network shares.

Then I navigated to that share in Nautilus File Browser, found the file, and double-clicked it.

An "Opening..." dialog shows up in the Gnome panel, although it disappears a few seconds later and nothing at all happens.

So I then right-click on the file, and try out "Open with Other Application..." and pick Inkscape out of the bunch.

Inkscape does show up, but with a blank slate... Didn't even open the file. :(

---

### Post by wylfing on 2005-10-12
Ah, there must be some older widget usage going on with Inkscape and Gaim.

A possible workaround is doing things the "old fashioned" way of explicitly mounting the Windows shares. Try installing linneighborhood. You can use that to browse for shares and mount them under your home directory. Then you should be able to use them without a problem.

---

### Post by skirkpatrick on 2005-10-12
That's odd.  This machine is still running Hoary and I've got a folder bookmarked and I can see it in the Open dialog of Inkscape.  It shows up in the left-hand box of mount points.

---

### Post by wylfing on 2005-10-12
Yeah, but try opening/saving files on that share. Doesn't fly.

---

### Post by JazzCrazed on 2005-10-13
Back again! Sorry for my hiatus... I've run into a barrel of problems with my networking - but that's a tale for [another thread]("http://ubuntuforums.org/showthread.php?t=60484&page=6").

I've installed linneighborhood (and smbfs, its dependency) via Synaptic, seemingly just fine. But I don't know how to run it now. #-o

Do I run it from terminal? Or is it suppose to show up in the Applications menu in Gnome?

Thanks for your gracious help!

---

### Post by Robgould on 2005-10-13
Have you tried mounting the share directly by adding it to your fstab file?

open the file:

```
sudo gedit /etc/fstab
```

Add code to the end:

```
//windowsip/share  /mnt/point  smbfs  rw,username=xx,password=xx,gid=xx,uid=xx  0 0 
```

You need to know the IP of you windows box and the share name.  You also need to set the windows IP to be static so that you do not have to change this code everytime it changes.  I don't mean you internet IP, I mean your LAN IP.

saave the file and close.  Mount the new share:

```
sudo mount -a
```

That will mount everything in your current fstab configuration.  If this works, it will autmatically mount the share to your filessytem when you boot.  You will know if it worked this time because it will show an icon for the share on your desktop.  If it does not work then something is wrong in your fstab entry.

This is diffent than connecting the sever, this mouts it to your filesystem so that you can access it just like you would any other file on your system.  Hope this helps.

---

### Post by Robgould on 2005-10-13
Couple of things I forgot about the fstab entry.....the username and password part is for your windows username and password.  The UID and GID are from your linux username.


the /mnt/point part is where you want it to be in your file system.  /mnt  is a standard directory.  Create a folder in that directory called whatever you want, say winxp.  Then list that part as /mnt/winxp and that is where the share will be mounted.

You may have to change the rights of the /mnt directory to create a folder.  If you do:

```
sudo chmod 777 /mnt
```


CAUTION that will give everyone rights to that folder.  If you need a more complex security setting let me know.  For instance 775, would limit write access to only the owner and users in that group.

Again, hope this helps.

---

### Post by JazzCrazed on 2005-10-13
Robgould,

Thanks for the tip, although I did try this following ubuntuguide.org: [http://ubuntuguide.org/#automountnetworkfoldersall](http://ubuntuguide.org/#automountnetworkfoldersall)

It checks for my login in .smbcredentials. That doesn't seem to pose a problem... But it does have a problem finding the share; I get a:

```
mount: special device //192.168.1.102/clients does not exist

```

...where 192.168.1.102 is the ip of the server, and clients is the name of the share. I've checked this several times to make sure. :(

BTW, the server is Windows 2000, and it's a domain controller, so I'm assuming that the login is the same as my login for the domain. After all, that login works for the Places->Connect to Server option in Gnome (which also asks for the domain name). Do I have to put the domain somewhere in the fstab?

Much thanks...

---

### Post by Robgould on 2005-10-13
I am not sure about a domain.  I got the smae error on my workgroup because my winxp settings were wrong.  I had to make sure that my share was actually shared.  I have no experience in a domain environment, sorry I could not be of more help.

---

### Post by wylfing on 2005-10-13
Linneighborhood does the same thing, only without having to mess with your /etc/fstab file -- i.e., it mounts SMB shares. Plus it's nice and graphical. 

If it's not showing up in your Gnome menu, you could launch it from a terminal by typing linneighborhood. (It's possible there's some goofy capitalization of the command name. I seem to recall something like that.) If it's something you run a lot, then make a launcher for it on your Desktop by right-clicking and choosing Create Launcher. I'm sure you can figure it out from there.

I also noticed a Nautilus script that mounts SMB shares. You can find out more about it here: [http://g-scripts.sourceforge.net/cat-filesysmgt.php](http://g-scripts.sourceforge.net/cat-filesysmgt.php)

Good luck.

---

### Post by JazzCrazed on 2005-10-14
wylfing,

The command is actually LinNeighborhood, and it ran just fine - so long as I was sudo!

I can use it to mount my shares on the W2K server to my home folder, and they're easily accessible for read/write (provided I set it up with the proper permissions in LinNeighborhood) in practically all applications! You're my savior!

One thing I'm curious of is whether these will be mounted on boot. I'll play around with it some more...

Thanks a billion...

---

### Post by wylfing on 2005-10-14
I'm glad LinNeighborhood did the trick for now. If you need to use this share *all the time*, however, as it seems from your comment about getting this established at boot time, you might want a more automatic solution.

I re-read your attempt at putting the share in /etc/fstab. The username and password are the ones you'd use to log in to the Windows box. Make sure you have the package smbfs installed (sudo apt-get install smbfs). 

You can also check what exactly your Linux box thinks the name of the share is by running [FONT="Courier New"][COLOR="DimGray"]smbclient -U username -L computername[/COLOR][/FONT], where username is the name you'd use to log in to the Windows box and computername is the name of said Windows box. You'll be prompted for a password, which is the password that goes with your Windows username. This should print out a list of all the shares available on the Windows machine.

It would probably also be advisable to put the IP address of your Windows server into /etc/resolv.conf so thereafter you can simply refer to it by its name.

---

### Post by JazzCrazed on 2005-10-14
wylfing,

Thanks for the tips. I guess I don't *really* need to have these shares loaded on boot. After all, this is...ahem...a laptop I'm using it on.

I think I was just put off by the redundancy of having to load up LinNeighborhood after every startup.

By the way, I added LinNeighborhood as a launcher, putting in  "LinNeighborhood" as the command; however, double-clicking the launcher launches nothing. I also tried "sudo LinNeighborhood," with the same result, and I checked the "run in terminal" option, as well, to no avail. :confused: Ah well, it's no biggie - launching from terminal will give me more typing practice. ;)

---

### Post by Robgould on 2005-10-14
One thing you could try to run this on boot is to go to system -> preferences -> sessions.  Select the startup programs tab and add the command there.  Hope it works for you.

---

### Post by Robgould on 2005-10-14
also, in your launcher, try listing the full path to the file in the command.  That should resolve your issue.

---

### Post by JazzCrazed on 2005-10-16
Hi Robgould,

Tried absolute path in the launcher, but no dice. :(  Not with "sudo," at least - which I think I need in order to run it correctly (without sudo or being root, the program loads, but doesn't allow me to browse the network; running as sudo or root *does* let me browse networks).

Any idea how to have launchers launch programs as sudo?

Thanks!

---

### Post by wylfing on 2005-10-16
Use gnome-sudo instead of sudo. (I should have said that originally, but I had forgotten LinNeighborhood needs root priveleges.)

---

