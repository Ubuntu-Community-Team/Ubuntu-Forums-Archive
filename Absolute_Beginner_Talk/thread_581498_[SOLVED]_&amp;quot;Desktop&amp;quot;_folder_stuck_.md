---
title: "[SOLVED] &amp;quot;Desktop&amp;quot; folder stuck in Trash"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Sabretooth on 2007-10-19
I did a clean install of Gutsy and everything seems to proceeding normally, except for this. I typically like my "Home" folder as empty as possible, so I deleted all the folders (including, accidentally the Desktop folder). All the other folders disappeared from the Trash normally, but the Desktop folder is stuck there. I delete it, and it reappears in the Trash bin within 10-20 seconds - Its annoying and creepy at the same time.

I can't seem to find a way to restore it, and the "Cut" and "Delete from Trash" options are grayed out. Like I've said before, if I Empty Trash, it reappears after some time. Also, in my Nautilus, if I click on "Desktop" in the left pane, it takes me to /home/(username)/.Trash/Desktop.

I'm no expert at sudoing and rooting my way around, so any help in getting rid of this ghostly folder will be appreciated!

**Problem Solved!**

Before we start, I think we should start with my problem in post #8. Read that and check the desktop_is_home_dir entry, log out and log in. Your home directory should have become your desktop, most likely. If not, I can't help. :(

1. First, enter this code into a Terminal:
```
sudo gedit ~/.config/user-dirs.dirs
```
2. Look for this entry: XDG_DESKTOP_DIR. Make it like this: XDG_DESKTOP_DIR="$HOME/Desktop"
3. Now log out and log back in. For me, this caused a Nautilus crash - i.e. the desktop disappeared and the nautilus browser wasn't working. So continue:
4. Open up System>Administration>System Monitor and in Processes, look for Nautilus. Stop it completely. If it does not exist, run Nautilus through Terminal (it should not have any effect, don't sudo it) and then stop it.
5. Run Nautilus via Terminal and it should be working furever.

---

### Post by mikeyphi on 2007-10-19
Two things to try!!

open your .trash folder-not the trashbin (view hidden folders!) right click/delete
if that fails - try opening the trash folder in a terminal and use the 'rm filename' command

---

### Post by true_friend on 2007-10-19
Another Idea try to restore it as a root.
open run box by Alt + F2 give this command
gksudo nautilus
go to your home and then trash try to restore that folder.
Regards

---

### Post by duartemolha on 2007-10-19
Well I no expert in linux or ubuntu but I do not think it is advisable to delete that folder... it is an important part of you home folder and everytime something is saved in your desktop the systems assumes the folder is where it should be.

I would advice you to open a terminal window and write:

1) cd /home/(username)/.Trash/
2) sudo mv Desktop /home/(username)


Hope this help.

Duarte

---

### Post by Beggar on 2007-10-19
```

sudo mv ~/.Trash/Desktop ~/

```

---

### Post by Sabretooth on 2007-10-20
Okay, I tried out the solutions, none of them are working:

mikeyphi: I deleted it from there, it reappears. :( I tried rmdir to take it out and it comes back later, again.

Rest: I went through root, but can't find a "Restore" option anywhere. Cut is available, and when pasted, creates a newfolder in my username folder, but it doesn't have the "Desktop" folder icon (check it out at your place). Moving does the same thing, obviously.

This is really getting at me. How do you restore things from Trash?

---

### Post by khabarkhan on 2007-10-20
> **Sabretooth said:**
> Okay, I tried out the solutions, none of them are working:

mikeyphi: I deleted it from there, it reappears. :( I tried rmdir to take it out and it comes back later, again.

Rest: I went through root, but can't find a "Restore" option anywhere. Cut is available, and when pasted, creates a newfolder in my username folder, but it doesn't have the "Desktop" folder icon (check it out at your place). Moving does the same thing, obviously.

This is really getting at me. How do you restore things from Trash?

Hi
I have the same problem. I suddenly delete Desktop folder from (username) folder and then try to restore it but i can't. So when I try to copy some files to my Desktop I get some error that said : I can't copy file in trash..
Please help

---

### Post by Sabretooth on 2007-10-20
**Update**

I don't remember what I did, but things have changed since I booted the system some two minutes ago. My Trash is empty, thankfully, but a new problem has arrived.

Ubuntu is for some reason, detecting my home/username folder as the Desktop folder and all its contents are splashed across my desktop. :( Also, the "username" folder entry you have in Nautilus' explorer pane is missing, and clicking on the desktop folder takes me there.

The only thing I remember doing is disabling "volumes_visible" in the Nautilus entry in the Configuration Editor, to keep my actual desktop completely clear. So I'm guessing that the solution must be like this:

1. Create a Desktop folder in my username folder.
2. Configure Nautilus to handle that folder as the Desktop folder.

I believe that should work, now the question is, how?

**Update 2**

I tried both enabling and disabling "desktop_is_home_dir" in nautilus preferences in the Configuration Editor. No effect.

---

### Post by khabarkhan on 2007-10-20
2. Configure Nautilus to handle that folder as the Desktop folder.

Would you please explain more? How can I do that. (I have no knowledge about Linux (; )

---

### Post by khabarkhan on 2007-10-20
> **khabarkhan said:**
> 2. Configure Nautilus to handle that folder as the Desktop folder.

 )

Would you please explain more? How can I do that. (I have no knowledge about Linux (;

---

### Post by tonywhelan on 2007-10-20
> **Beggar said:**
> ```

sudo mv ~/.Trash/Desktop ~/

```

My Desktop also ended up in the Trash though I don't recall putting it there! 

I used the above command to move it back successfully, but like the first poster I now have all my Home folders sitting on the desktop. In gconf-editor, the Nautilus preferences has desktop_is_home_dir unchecked (false) which means that the desktop should reflect the contents of the Desktop folder rather than of the Home folder.
But it seems to take no notice of the setting.

It's not the end of the world ... but would be nice to find why it is doing this and how to fix it.

---

### Post by tonywhelan on 2007-10-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/154037](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/154037) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Sabretooth said:**
> **Update**

I don't remember what I did, but things have changed since I booted the system some two minutes ago. My Trash is empty, thankfully, but a new problem has arrived.

Ubuntu is for some reason, detecting my home/username folder as the Desktop folder and all its contents are splashed across my desktop. :( Also, the "username" folder entry you have in Nautilus' explorer pane is missing, and clicking on the desktop folder takes me there.

The only thing I remember doing is disabling "volumes_visible" in the Nautilus entry in the Configuration Editor, to keep my actual desktop completely clear. So I'm guessing that the solution must be like this:

1. Create a Desktop folder in my username folder.
2. Configure Nautilus to handle that folder as the Desktop folder.

I believe that should work, now the question is, how?

**Update 2**

I tried both enabling and disabling "desktop_is_home_dir" in nautilus preferences in the Configuration Editor. No effect.


See this link for a suggested fix (which I am  about to try myself in a minute)
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/154037](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/154037)

---

### Post by Sabretooth on 2007-10-21
Um, guys, I've included the solution in the first post. :D

---

### Post by khabarkhan on 2007-10-22
> **Sabretooth said:**
> 
**Problem Solved!**

Before we start, I think we should start with my problem in post #8. Read that and check the desktop_is_home_dir entry, log out and log in. Your home directory should have become your desktop, most likely. If not, I can't help. :(

1. First, enter this code into a Terminal:
```
sudo gedit ~/.config/user-dirs.dirs
```
2. Look for this entry: XDG_DESKTOP_DIR. Make it like this: XDG_DESKTOP_DIR="$HOME/Desktop"


Thank you so much. I just do 1 and 2 and in part 2 also change second line to this way : XDG_DOWNLOAD_DIR="$HOME/Desktop

then log out and log in again . And done. 
Great . nice job!!
Thanks again.

---

### Post by 23meg on 2007-10-26
This fixed the problem for me too; thanks.

Note: For graphical apps such as gedit, use *gksudo* instead of *sudo*.

---

### Post by crocco on 2008-05-11
Before...

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/.Trash/Desktop"
XDG_DOWNLOAD_DIR="$HOME/.Trash/Desktop"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"


After...

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"

Followed your instructions, and this did the trick.  Just wanted to actually show the changes!

---

### Post by oktapod on 2008-06-20
Re: Removing Items for Trash
Open your terminal and input the following commands to clean your Trash:

Code:

sudo rm -rf /home/your_user_name_here/.local/share/Trash/*

or

Code:

sudo rm -rf ~/.local/share/Trash/files/*

__________________
Steady movement is more important than speed, much of the time. So long as there is a regular progression of Stimuli to get your mental hooks into, there is room for lateral movement. Once this begins, its rate is a matter of discretion. 

It worked for me - Ubuntu 8.04 amd64. Hope helps you too.

---

