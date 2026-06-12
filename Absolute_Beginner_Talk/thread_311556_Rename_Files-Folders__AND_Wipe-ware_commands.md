---
title: "Rename Files-Folders  AND Wipe-ware commands"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by daktari on 2006-12-03
Using Dapper on a T23 laptop:


**1 - Intermittent renaming failures**

I can sometimes rename files and folders, sometimes not. Rebooting sometimes helps, sometimes not.  I've tried renaming files and folders by both
- rightclick->rename (overwrite), and
- rightclick->properties->basic (overwrite)  

No particular pattern to the failures that I can see - the problem is intermittent / unpredictable.


**2 - Wipe commands**

I installed "wipe" via terminal command line (apt-get install).  If there's  a GUI for it, I can't find it.  If there are Dapper terminal command lines to use it's basic functions, I haven't found them, e.g.:
- wipe a file
- wipe a folder
- wipe empty disk space


Thanks in advance for any steerage on either of these issues.

---

### Post by CatKiller on 2006-12-03
1: You've not really said what the problem is. Is it a permissions problem? A read-only filesystem problem? Any error messages at all?

2: You could try the wipe homepage: [http://abaababa.ouvaton.org/wipe/](http://abaababa.ouvaton.org/wipe/) or the wipe manpage (**man wipe**) for instructions on how to use it.

---

### Post by daktari on 2006-12-03
> **CatKiller said:**
> 1: You've not really said what the problem is. Is it a permissions problem? A read-only filesystem problem? Any error messages at all?

Don't know how to determine if its permissions / filesystem related.  If there's specific data or behaviors I should be looking at, fire away.

I can change file and folder names at one moment (or in one session), but not the next.  The same file or folder responds differently on different attempts to rename it. 

In most cases, I can change names of - say - between one and five files or folders in a session.  Then subsequent attempts fail.

/

Thanks for the wipe tips.

---

### Post by CatKiller on 2006-12-03
So what happens if you use ```
mv name1 name2
```?

I've never had any problems renaming files graphically though.

---

### Post by mssever on 2006-12-03
> **daktari said:**
>  **2 - Wipe commands**

I installed "wipe" via terminal command line (apt-get install).  If there's  a GUI for it, I can't find it.  If there are Dapper terminal command lines to use it's basic functions, I haven't found them, e.g.:
- wipe a file
- wipe a folder
- wipe empty disk space
The command shred does most of this, but it can't handle folders. I've made a wrapper around shred that can handle this. It's called shred-recursive and it's available from [my repository]("http://severance.homelinux.org/falcon/"). My tool is CLI-based, but you could probably come up with a Nautilus script to call shred-recursive.

I don't know about shredding free space, though. I've never tried to do that...

EDIT: to add my repo, add the following to /etc/apt/sources.list: ```
deb http://severance.homelinux.org/falcon main all
``` then do ```

wget http://severance.homelinux.org/falcon/3586F8CB.gpg -O- | sudo apt-key add -
sudo apt-get update
```Or, you can use the web interface at the above link to choose only what you want.

---

### Post by mssever on 2006-12-03
Here's a Nautilus script that calls shred-recursive from Nautilus. Save the following as ~/.gnome2/nautilus-scripts/Shred ```
#!/bin/bash
gnome-terminal -e 'shred-recursive $NAUTILUS_SCRIPT_SELECTED_URIS'
``` Make it executable (right-click > Properties > Permissions or chmod +x ~/.gnome2/nautilus-scripts/Shred). Select files to shred, right-click and choose Scripts > Shred.

I don't know off hand what will happen if you select files whose names contain spaces or special characters, as I haven't tested this script. shred-recursive is safe itself, I just don't know about the Nautilus script.

---

### Post by daktari on 2006-12-03
[QUOTE=CatKiller]
So what happens if you use ```
mv name1 name2
```?[/QUOTE]

The mv command worked for both file and folder renaming. Thanks!

[QUOTE=CatKiller]
I've never had any problems renaming files graphically though.[/QUOTE]

That problem still bugs me.  The only definable peculiarity I can see so far is that folders and files that I create often seem to have different permission combinations though I created them all under the same conditions and without specifying perm's.  I'll figger it out eventually.  Or not.

[B][I]Status: 
- Command line rename solution found / works
- GUI rename issue persists[/I][/B]


///


[QUOTE=mssever]
Here's a Nautilus script... (et al)[/QUOTE]

Thanks very much for the wipe steerage.  It will take me some time to absorb and use it.  

I'd try bcwipe for ease of use, but have had some peculiar experiences with it, some involving mal-code.
.

---

### Post by daktari on 2006-12-03
GUI File/Folder Rename Issue Addendum: Related Symptoms in GUI mode

Assume I've made one file rename attempt and failed: specifically, I got as far as typing the desired file name on the keyboard (e.g., "mystuff") but with no effect on the screen-displayed file name field.

Then - in the same session:

On the next file rename attempt on a different file - *in some instances* - when I start to type in a new file name (e.g., "otherstuff"), the *previously* typed file name ("mystuff") will appear in the file name field instead.

Go figure.

:-k 

.

---

### Post by daktari on 2006-12-10
GUI File/Folder Rename Issue Addendum #2: Found Work-Around

At some indeterminate point after successfully renaming a number of files or folders in GUI mode, it stops accepting any typing in the name field.

I found one work-around to this unexplained GUI aberration that seems to work without fail:

1 - right click file/folder name -> click rename

if the file/folder name field won't accept keystrokes, then

2 - open a text editor and type the new file/folder name
3 - cut or copy the new name from the text editor
4 - return to the GUI name field and paste it

/

[B][I]Status:
- command line rename (mv) works - solution found
- GUI rename issue persists, but found work-around[/I][/B]

.

---

### Post by CatKiller on 2006-12-10
> **daktari said:**
> At some indeterminate point after successfully renaming a number of files or folders in GUI mode, it stops accepting any typing in the name field.

That is bizarre. It might be worth reporting this as a bug against nautilus in either [Ubuntu's Launchpad]("https://bugs.launchpad.net/distros/ubuntu/+bugs") or [Gnome's bugzilla]("http://bugzilla.gnome.org").

They might have more idea about reproducability and cause than people here.

---

### Post by daktari on 2006-12-10
> **CatKiller said:**
> That is bizarre. It might be worth reporting this as a bug against nautilus in either [Ubuntu's Launchpad]("https://bugs.launchpad.net/distros/ubuntu/+bugs") or [Gnome's bugzilla]("http://bugzilla.gnome.org").

Thanks for the steerage. Here's the result.

Launchpad rejected every effort I made to make a bug report saying I hadn't registered (not true), also saying i wasn't assigned to a "group".

But Gnome Bugzilla worked - here's the report ID:
Bug 384600 – File / Folder Rename Issue - GUI mode
Opened by daktari
2006-12-11 03:17 UTC

---

