---
title: "Basic linux/ubuntu for a newbie"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by dooleydotdk on 2006-04-02
Hi

I completely new to linux, a leftover from the old ancient windows world. Ubuntu is installed, updated and running.

1) Recover icon. I've made a new user on my system which should only have access to browsing (firefox). It's seems that the user can remove the firefox icon. How do I (he/she) recover the icon? If not can the master account do it for the user?

2) Access partition. I have a logical partion (ntfs). Is'nt that auto-mounted? If not, how do I do it?

Sorry for the very basic questions, we all have to start somewhere :) 

kind regards 
Tom

---

### Post by catlett on 2006-04-02
Go here for info on mountimng your partition. These guides and how tos have been created by an Ubuntu forum member and they are very good.
[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)
I don't know about the permissions but if you want to get the icon back I can help. Go to the top and click on Applications. Scroll down to Internet. Scroll over to Firefox. Right click on Firefox. You will get a choice of adding the launcher to the panel (this puts the icon up top on the "task bar") or adding it to desktop (this will give you an icon on the desktop like in windows). You can do this to anything in the menu. You can scroll through the menu and right click on any entry and add it to the panel or desktop.
This link will send you to a thread with alot of info on how to find answers in the forum and internet.  [http://www.ubuntuforums.org/showthread.php?t=142716](http://www.ubuntuforums.org/showthread.php?t=142716)

---

### Post by dooleydotdk on 2006-04-02
Thanks for the answers.

according to my issue 1); the "problem" is that I've removed the "top tool bar". One solution is just creating a new account, but I'm curious if this could be fixed smarter. In other words I'm looking for a setup of a account in a "kiosk browser" sort of way; nothing should/could be changed even on the desktop. 

Tom

---

### Post by aysiu on 2006-04-02
Only KDE has kiosk mode, not Gnome.
Are you using Gnome?

---

### Post by dooleydotdk on 2006-04-03
Yes, I'm using Gnome. So you are right, I should ask this, in a Gnome thread or learn to start (and use) KDE. 

Thanks. 
Tom

---

### Post by IYY on 2006-04-03
Your icon problem can be easily solved. Icons in Gnome are stored as actual files, in the ~/Desktop/ directory (~ means your home directory, the full path is /home/yourname/Desktop/). These files are plain text files which you can create in any text editor (nano is a simple text editor for the command line).

If you want to copy your firefox icon to the user's desktop, first find out the name of the icon file in your account (might very well be firefox.desktop) then do this in the terminal:

sudo cp ~/Desktop/firefox.desktop ~/../otherusersname/Desktop

That's it. The other user should now have a firefox icon on their desktop, and they wouldn't be able to remove it since it belongs to you.

---

### Post by dooleydotdk on 2006-04-03
[QUOTE=IYY]
sudo cp ~/Desktop/firefox.desktop ~/../otherusersname/Desktop
[/QUOTE]

That sounds like a nice solution. An really newbie question :D would be how to issue a line command in/from linux/ubuntu/gnome? Back in windows I had the command prompt for using DOS commands.

Tom

---

### Post by dooleydotdk on 2006-04-03
[QUOTE=dooleydotdk]...how to issue a line command in/from linux/ubuntu/gnome? Back in windows I had the command prompt for using DOS commands.[/QUOTE]

I've found it! The terminal. :-D 
Tom

---

### Post by catlett on 2006-04-03
I put a "short cut" for the terminal on my launcher. It's as easy as scrolling through apps,accessories,terminal and then right clicking on the terminal. You'll get three options. Choose add to the panel to get it up top on the launcher or add to desktop to get a windows type of short cut on your desktop. For me it's quicker to access the terminal through the shortcut than scrolling through the menu.

---

### Post by dooleydotdk on 2006-04-07
[QUOTE=IYY]sudo cp ~/Desktop/firefox.desktop ~/../otherusersname/Desktop[/QUOTE]

Hi again
When I change dir (cd Desktop) and ls (list) I dont find firefox.desktop. It's on my desktop! As a result the sudo command fails with '...not found'. Am I misunderstanding something?

---

### Post by IYY on 2006-04-07
Well.... I have a firefox.desktop in my Desktop folder. If you want, you could just copy my file:

```

[Desktop Entry]
Encoding=UTF-8
Name=Firefox Web Browser
GenericName=Web Browser
Comment=Firefox
Exec=firefox %u
Terminal=false
MultipleArgs=false
Type=Application
Icon=mozilla-firefox.png
Categories=Application;Network
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;x-directory/webdav;x-directory/webdav-prefer-directory;image/gif;image/jpeg;image/png
StartupWMClass=Firefox-bin

```

You could place this right on your users desktop if you use

> sudo nano /home/otherusersname/Desktop/firefox.desktop

And then just paste that code in and save.

---

### Post by dooleydotdk on 2006-04-07
Getting curious. My properties on firefox says something like '/home/myuser/Desktop'. How come that I cant see it on a ls command?
Any ideas? 
Tom

---

### Post by aysiu on 2006-04-07
Try ```
cd ~/Desktop
ls -a
```

---

### Post by dooleydotdk on 2006-04-07
[QUOTE=aysiu]Try ```
cd ~/Desktop
ls -a
```[/QUOTE]

Still with -a nothing but my firefox update script appears

---

### Post by dooleydotdk on 2006-04-07
The 'sudo nano /home/otherusersname/Desktop/firefox.desktop' with a copy paste works. Still I'm curiuos why I cant see this desktop code on my own account.
Thanks
Tom

---

### Post by dooleydotdk on 2006-04-07
[QUOTE=dooleydotdk]The 'sudo nano /home/otherusersname/Desktop/firefox.desktop' with a copy paste works.[/QUOTE]

But still it seems that the user can delete the icon. In useradministration no privileges is 'tagged'.

---

### Post by aysiu on 2006-04-07
Try this: ```
sudo chown root:root /home/otherusersname/Desktop/firefox.desktop
sudo chmod 755 /home/otherusersname/Desktop/firefox.desktop
``` This other user won't be able to delete the icon if it belongs to root.

---

### Post by IYY on 2006-04-07
How did you add the icon to your own desktop? Did you drag it from some menu/panel, or was it there by default? 

Basically, there are several icons which you can see on the desktop without having actual icon files. I think you can have your home folder, computer and mounted volumes. You can check/uncheck the visibility of these icons using gconf-editor.

---

### Post by steve.horsley on 2006-04-07
[QUOTE=aysiu]Try this: ```
sudo chown root:root /home/otherusersname/Desktop/firefox.desktop
sudo chmod 755 /home/otherusersname/Desktop/firefox.desktop
``` This other user won't be able to delete the icon if it belongs to root.[/QUOTE]
Sorry, that's not true. I think it's because the user owns the directory, and deleting a file involves writing to the directory, not the file being deleted.
> steve@dingly:~$ sudo touch testfile
Password:
steve@dingly:~$ ls -l testfile
-rw-r--r--  1 root root 0 2006-04-07 22:32 testfile
steve@dingly:~$ rm testfile
rm: remove write-protected regular empty file `testfile'? y
steve@dingly:~$ ls -l testfile
ls: testfile: No such file or directory

So I'm not really sure how you'd protect the desktop from deleting icons. Maybe have a script that deletes the entire directory tree and then untars it from a safe tar file as the user logs in?
rm -rf ~/.
tar xf /home/user.tar

---

### Post by IYY on 2006-04-07
> Sorry, that's not true. I think it's because the user owns the directory, and deleting a file involves writing to the directory, not the file being deleted.

Right. I didn't really think this one through. ](*,) 

I guess he'll have to create the desktop directory in the other user's directory, with his own account using sudo.

Something like

you@yourmachine:$ sudo mkdir /home/otheruser/Desktop
you@yourmachine:$ sudo cp /home/you/Desktop/firefox.desktop  /home/otheruser/Desktop

---

### Post by aysiu on 2006-04-07
[QUOTE=steve.horsley]Sorry, that's not true. I think it's because the user owns the directory, and deleting a file involves writing to the directory, not the file being deleted.[/QUOTE] Wow. Is that true? That's crazy.

So if I own a directory, it doesn't matter if someone creates a root-owned file within directory (with no write permissions from other users)--I can still delete it because I own the directory? Crazy.

Well, you learn something new...

---

### Post by nanotube on 2006-04-07
from the manual page of chmod ("man chmod")

> STICKY DIRECTORIES

       When  the sticky bit is set on a directory, files in that directory may
       be unlinked or renamed only by root or their owner.  Without the sticky
       bit,  anyone able to write to the directory can delete or rename files.
       The sticky bit is commonly found on directories, such as /tmp, that are
       world-writable.

so, all you need to do is chmod the Desktop directory of the user to have the sticky bit.
```
chmod 1755 /home/username/Desktop
```

that, coupled together with the chowning of the file to root:root, should prevent the user from deleting any files in the Desktop directory that are not owned by that user.

---

### Post by aysiu on 2006-04-07
Thanks, nanotube.

This thread has been really educational for me, even though I'm not the OP.

---

### Post by dooleydotdk on 2006-04-08
Hi
I tried 
sudo chown root:root /home/otherusersname/Desktop/firefox.desktop
sudo chmod 755 /home/otherusersname/Desktop/firefox.desktop
sudo chmod 1755 /home/otherusername/Desktop

I'm not alowed to do chmod 1755 /home/otherusername/Desktop without the sudo

User is still able to delete icon. Should the sticky bit (I guess it is the 1 in 1755) also be set for the icon?

---

### Post by dooleydotdk on 2006-04-08
[QUOTE=dooleydotdk]Should the sticky bit (I guess it is the 1 in 1755) also be set for the icon?[/QUOTE]

sudo chmod 1755 /home/otherusersname/Desktop/firefox.desktop
dont seem to have any effect in preventing the user from sending the icon to wastebasket ](*,)

---

### Post by nanotube on 2006-04-08
hmm, strange... i would think it /should/ work.
but ok, if you do the following, then for sure it should work:

```
sudo chown root:root /home/otherusersname/Desktop/firefox.desktop
sudo chmod 755 /home/otherusersname/Desktop/firefox.desktop
sudo chmod 1777 /home/otherusername/Desktop
sudo chown root:root /home/otherusersname/Desktop
```

basically, that makes the owner of the desktop dir also root, and gives world-write permissions to the dir so the user can store other files in it (otherwise only root can). 

but yea, that's strange... i guess we need a Real permissions expert to figure out why that original sticky bit idea does not work - because by the man page, it should...

---

### Post by dooleydotdk on 2006-04-09
This works! :D 

Thank you so much for takin' your time to help solving the task and explaining it so even I get the point...

Out of curiosity: can I 'reverse' the bloking by issuing the chmod with appropiate values?

I'll now take my time to read about installing packages like java and configuring firewall. It seems like nanotube has a very good newbie(me) howto 'My Comprehensive Ubuntu Breezy Customization Howto' at [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles)

By the way, I still cant figure out why I by default dont have the firefox.desktop file in my Desktop folder, even though the icon is on my desktop. Anyway I've made an extra icon with copy/paste in nano, like described earlier in this post.  

Thanks, Tom

---

### Post by nanotube on 2006-04-09
[QUOTE=dooleydotdk]This works! :D 

Thank you so much for takin' your time to help solving the task and explaining it so even I get the point...

Out of curiosity: can I 'reverse' the bloking by issuing the chmod with appropiate values?
[/quote]
yes, if you just chown the Desktop directory to be owned by the user, instead of root, he will be able to delete that file. 

> I'll now take my time to read about installing packages like java and configuring firewall. It seems like nanotube has a very good newbie(me) howto 'My Comprehensive Ubuntu Breezy Customization Howto' at [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles)

heh, glad you are enjoying it. :)

---

