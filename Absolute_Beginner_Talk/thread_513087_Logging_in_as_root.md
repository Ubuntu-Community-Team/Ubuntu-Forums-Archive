---
title: "Logging in as root"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-07-30
I need to log in as root to delete a file I don't have privelages for.

I am aware of the dangers.

This is what I was told

> There search for the user "root". U will find it. After choosing root, click on "properties" and change the password to something u want. there will be a system generated random root password which you have to erase and set a new one of your choice. once you are done come out of that and close all windows.
THEN, again from start menu go to System --> Administration --> Login Screen Setup.
There go to the "security" tab and CHECK "allow root to login with GDM". Close all windows and log out of GNOME and on to GDM.
type root, root's password that u had set and log in as root!

I do not see "allow root to login with GDM" on the Security tab. Please help.

---

### Post by mcduck on 2007-07-30
No, you don't need to log in as root to do that. Actually you don't need to log in as root to do anything.

(And you never ever should log into desktop as root anyway!)

To open file manager with root privileges so you can remove those files hit Alt-F2 and run "gksudo nautilus". Be careful with that, and make sure the files you're about to remove are not needed by your system.

edit: You may want to read this one: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Cheese Roller on 2007-07-30
Can you tell me what this process does?

---

### Post by mcduck on 2007-07-30
> **Cheese Roller said:**
> Can you tell me what this process does?

Alt-F2 opens the 'Run' dialog that allows you to run commands. You could just use the terminal for same thing.

'gksudo' is a command to used to open graphical programs as root, it pops up a dialog asking for you to enter your password. Nautilus is the file manager used in Gnome desktop.

So running 'gksudo nautilus'  will ask for password and the open the file manager as root. Now you can use it to do any tasks you would do as root, but instead of running the whole desktop as root you only run the single file manager window as root. And of course this way you don't even need to enable the root account so your whole Linux install will be more secure this way, and you don't need to log in to separate account to do admin tasks.

---

### Post by Cheese Roller on 2007-07-30
Well, I'm not too good with the command prompt yet...

Is there a way I can just log in as root?

---

### Post by Eddy Dean on 2007-07-30
You really don't want to log in as root. It's too dangerous.
Log in as a regular user, then hit Alt-F2. You will get a small window with a textbox at the top. Type ```
gksudo nautilus
``` in there, then hit enter. The screen will go a bit darker and in the middle there will be a screen asking for your password. Fill in your password (the regular password, not the root password) and hit enter. Now a file manager will open. In this file manager you can browse to the file you want to delete, select it and hit the delete key.

---

### Post by Cheese Roller on 2007-07-30
Okay, I guess I'll trust you. I heard root is dangerous as long as you're connected to the internet. I pulled my plug just in case.

What IS the danger of logging in as root?

Also, once I type this command, how do I get out of this mode and make things normal again?

---

### Post by Vague on 2007-07-30
As has been stated before, the root account is, by default, disabled in Ubuntu.  It's recommended that you don't change this, which you've said you realized, but in your case you don't need to.  Like everyone else has said, "gksudo nautilus" will allow you to run Nautilus with root priveleges.  Sorry if this comes off as a bit rude, but logging into GNOME as root is a rather rear-end-backwards way of doing something that is extremely easy to do with gksudo.  You really don't need to be all that good with the command prompt to do this.  Using mcduck's instructions you won't even have to use the terminal.

Edit: The danger of logging in as root is, essentially, that you always have root privileges.  Generally, it's better to only have the ability to install things, delete files, etc. when you actually want to do it.

You don't need to do anything to get out of it, other than close the Nautilus window.

---

### Post by Eddy Dean on 2007-07-30
To get out of this mode you just close the file manager. Root is the only account that can actually damage your system. As a regular user you can't modify your system (Except for some preferences, for example keyboard layout, mouse speed etc), but as root you'll be able to remove programs etc, or even make your system totally broken.

Don't worry about too much, you'll be just fine. Don't forget to close the file manager after you've removed the file (cross at the top-right of the screen ;)), else you'll still have root privileges in that window!

---

### Post by Cheese Roller on 2007-07-30
Okay guys, I did what you told me and it froze after I click inside a folder.

I had to end the application, now it wont come up again.

What went wrong?

---

### Post by doomster on 2007-07-30
if after all you wanna have the option to login as root, for your own reasons,this is the way you can do this:
go to System > Administration>Login window
on the 5th tab called "security" enable the option "Allow local system  administrator login"
logout and relogin as root :)

p.s: i will aggree with the above ones, saying you dont have a reason loggin as root. everything you wanna do can be done with a little knowledge and the help of "sudo" and "gksudo" commands

have fun

---

### Post by Cheese Roller on 2007-07-30
O-KAY. It crashed. It came back up but that was really really wierd... I am gonna try this again. Something is clearly wrong with my computer though.

Okay I typed that code again, but the load times are terrible.

It just started doing this an hour ago.

---

### Post by Cheese Roller on 2007-07-30
Yeah, it froze again as soon as I  clicked a folder, what should I do guys?

Is there someway I can just delete it by typing in something?

it's located in "/media" it is a whole folder that should not be there, could be the source of my problems. The file came from a CD I put in the computer that is currently not inserted in the drive. I want to get rid of it.

---

### Post by ike on 2007-07-30
> **Cheese Roller said:**
> Is there someway I can just delete it by typing in something?

You can open up a terminal window and type
```
sudo rm -r /media/folder/
```
where you replace "/media/folder/" with the folder you wish to delete.

But, be careful with this. Using sudo (and gksudo) could potentially harm your system if you make a mistake.

---

### Post by Vague on 2007-07-30
Yes, there is a way to delete things simply by typing something.  Open up a terminal window and enter ```
sudo rm /path/to/file
``` replacing /path/to/file with, obviously enough, the actual path to the file, and keeping in mind that you are running this with root privileges.  There are other flags you can use with it, as well.  If you're all that interested, open up a terminal and enter ```
man rm
``` and it'll tell you all about them.  (Edit: didn't see ike's post up there.)

Your situation, though, has me a bit confused.  What folder is in /media that shouldn't be there?

---

### Post by Cheese Roller on 2007-07-30
Which one o f those do I use, they're different.

---

### Post by Cheese Roller on 2007-07-30
Okay guys. I did that command. It says there is no such file or directory. Yet I  can see it.

Edit: I just realized what the problem is... The folder's name has spaces in it, and the computer counted that whole thing as being more than one folder.

What would I do with spaces?

---

### Post by Vague on 2007-07-30
> **Cheese Roller said:**
> Which one o f those do I use, they're different.

rm is just the command for remove.  -r is the flag for "recursive," which allows you to remove a directory and all of its contents (rm by itself will only allow you to delete files or empty directories).  I'm still wondering what you're trying to delete, though.  /media is where your CD-ROM should generally be mounting to (/media/cdrom, I believe).

---

### Post by aysiu on 2007-07-30
Let's say the name of the folder with spaces in it is *Folder with spaces in it*, you can put in backslashes to indicate that the folder name keeps going (otherwise, it assumes the end of the first word is the end of the folder name): ```
cd /path/to/Folder\ with\ spaces\ in\ it
sudo rm -r *
```

---

### Post by Cheese Roller on 2007-07-30
> **Vague said:**
> rm is just the command for remove.  -r is the flag for "recursive," which allows you to remove a directory and all of its contents (rm by itself will only allow you to delete files or empty directories).  I'm still wondering what you're trying to delete, though.  /media is where your CD-ROM should generally be mounting to (/media/cdrom, I believe).

That is correct, there is a disc mounted that I already took out of the drive. Can't get rid of it.

---

### Post by aysiu on 2007-07-30
We're going to need more details, Cheese Roller. What's the path to the file you're trying to delete? What's the file called? Is it on a CD-ROM? Or is it on an external USB drive? What do you mean by "disc mounted"?

---

### Post by Cheese Roller on 2007-07-30
Okay, the file came from a CD Drive that was mounted.

After right removing the disc from the disc drive, Ubuntu says it is unable to unmount disc, unable to delete directory.

My computer has been acting really REALLY strange lately since this happened and I think it might be the source of it.

The CD was a Windows program (that I am honestly not sure was trustable) so I think I am going to get rid of the disc as soon as I solve this problem.

But yes, that  is the story.

---

### Post by aysiu on 2007-07-30
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
sudo fdisk -l
mount
df -h
cd /media
ls
```

---

### Post by Cheese Roller on 2007-07-30
Do I enter all of that at once? Or one after the other?

---

### Post by meierfra on 2007-07-30
one after the other.

---

