---
title: "All my noob questions in one sweep"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by englishmen on 2006-10-22
I hope this post will clear up all the little questions that i have up.

1* In windows xp i use ccleaner to remove the mru lists from programs I use, how would I remove mru's from programs in ubuntu?

2* I also use eraser to _actually_ delete files, how would i do this in ubuntu?

3* Can someone please explain how i delete the "example" folder within my Home folder?

4* Related to the above how do i delete a file/folder that is not located in anything but my home folder?

5* I have download last.fm and to run it all I need to do is run the file lastfm. I have put the extracted folder in my home folder and placed a link to the file lastfm in the sound & video menu. I would have preferred to install last.fm like the other apps so the last.fm folder would not be just lying around. How would I go about hiding the last.fm folder(just so i can have a tidy home folder).

Thanks for any help you can supply.

---

### Post by d3v1ant_0n3 on 2006-10-22
Unfortunately, the only one here I can help you with is the last problem (and only that because I spend too much time reading these forums....

Change the name of the lastfm folder so it has a '.' in front of it- for example, if the folder is called 'lastfm', rename it to '.lastfm'. This will make it a hidden folder. I think. You'll have to redo any launchers to have assigned to this folder tho'.

---

### Post by David_T on 2006-10-22
1)  I don't know if such a thing exists yet.  I think you'll find that the prefs for most of your apps will exist in your home folder in plain text files.  You can do ls -a in your home folder to find some of these folders.  Seems like you could write a script to do what you need once you find where the mru lists are for your most-used programs.  Firefox will erase all your private data for you, but you probably already knew that.
2) sudo apt-get wipe.  I think this is in the universe repository.
3) rm -rf Examples.  Careful you don't type rm -rf *.  Check out man rm for more info.
4) You will need to sudo to do that.
5) Rename it to .last.fm and change the symlink to reflect that.

---

### Post by Kulgan on 2006-10-22
> 
I hope this post will clear up all the little questions that i have up.

1* In windows xp i use ccleaner to remove the mru lists from programs I use, how would I remove mru's from programs in ubuntu?

2* I also use eraser to actually delete files, how would i do this in ubuntu?

3* Can someone please explain how i delete the "example" folder within my Home folder?

4* Related to the above how do i delete a file/folder that is not located in anything but my home folder?

5* I have download last.fm and to run it all I need to do is run the file lastfm. I have put the extracted folder in my home folder and placed a link to the file lastfm in the sound & video menu. I would have preferred to install last.fm like the other apps so the last.fm folder would not be just lying around. How would I go about hiding the last.fm folder(just so i can have a tidy home folder).


I'm no guru, but I can help with a couple things:

1: Have no idea, but I think that Places -> Recent Documents -> Clear Recent Documents could be a start...

2: I take it you mean actually delete them, rather than sending them to the Trash? That would be select them -> Shift + Delete

3: In the terminal (Applications -> Accessories -> Terminal) type "sudo rm -rf /home/<username>/Examples" (without quotes), then type in your ROOT password. (the password doesn't actually appear, even in asterixes, which is rather odd, but so be it).

4: I'm not all that sure you want to do this, but here goes...
For just deleting it, use the above, just replace /home/<username>/Examples with whatever directory or file you want to delete. If you want to edit contents, you have to CHMOD: "chmod 777 /home/<username>/Examples/*" for the contents of the Examples folder ('*' stands for 'all').

5: If it does not matter what the folder name is, just add a full stop in front of it, so it becomes ".last.fm", and you can update the link in the menu. 

Hope this helps, though someone has probably beat me to the post :P

-K

---

### Post by Kulgan on 2006-10-22
> someone has probably beat me to the post :P

Not one, but two!

---

### Post by aznboi on 2006-10-22
u dont need ccleaner on ubuntu, but for firefox if you want ure cache and stuff deleted at the push of a button download and install this:
[https://addons.mozilla.org/firefox/1484/](https://addons.mozilla.org/firefox/1484/)

then add it into somehwere in ure navigation panel in firefox, and click it and itll bring up a checklist of stuff u might wanted deleted and u tick/untick things u want deleted and itll do ti for you.

to delete the examples folder, login as root and goto /home/username/ and move the examples folder to the trash.

---

### Post by CatKiller on 2006-10-22
> **englishmen said:**
> I hope this post will clear up all the little questions that i have up.

1* In windows xp i use ccleaner to remove the mru lists from programs I use, how would I remove mru's from programs in ubuntu?

It took me quite a while to work out what "mru" meant. Just use Places -> Recent Documents -> Clear Recent Documents: > **Clear the Recent Documents list?**

If you clear the Recent Documents list, you clear the following:

• All items from the Places &#8594; Recent Documents menu item.
• All items from the recent documents list in all applications.

> 2* I also use eraser to _actually_ delete files, how would i do this in ubuntu?

I'm usure of exactly what you mean. If you mean "not send to Wastebasket", then use Shift-Del or **rm**. If you mean "overwrite the file afterwards" then use **shred**.
> **NAME**
       shred - overwrite a file to hide its contents, and optionally delete it

**SYNOPSIS**
       **shred** [_OPTIONS_] _FILE_ [...]


> 3* Can someone please explain how i delete the "example" folder within my Home folder?

Just delete it, man. It's a link that gets put in everyone's Home folder. If you don't want it in new users' Home folders either, delete /etc/skel/Examples.

> 4* Related to the above how do i delete a file/folder that is not located in anything but my home folder?

[Use]("http://www.psychocats.net/ubuntu/permissions") [sudo]("https://help.ubuntu.com/community/RootSudo").

> 5* I have download last.fm and to run it all I need to do is run the file lastfm. I have put the extracted folder in my home folder and placed a link to the file lastfm in the sound & video menu. I would have preferred to install last.fm like the other apps so the last.fm folder would not be just lying around. How would I go about hiding the last.fm folder(just so i can have a tidy home folder).

I'll take your word for it that that's how it works. A friend keeps trying to get me to track what I listen to, but I haven't bothered yet. But you can create a file in the folder that contains the file you want to hide called .hidden. In this file, write the name of the file you want to hide. It now won't show up in Nautilus unless you select "Show hidden files". Saves you having to re-do any launchers or scripts.

---

### Post by englishmen on 2006-10-23
Wow thanks everyone for the help.

Concerning my first question, i wasnt aware that using Places -> Recent Documents -> Clear Recent Documents: also cleaned programs mru lists as well. I tested it and it does for some but not for others and as i don't know how to write a scrip i guess it will do.

On actually deleting files/folders i should have said securely deleting them, i got wipe as David_T suggested but i cant seem to find a link for it anywhere in any menu. Does any know how to use it?

Concerning shred is there not some way i can add new entry to the trash bins context menu which says "Shred trash" clicking it will give me a confirmation box which once confirmed will securely shred all items in the trash. Basically like eraser but for ubuntu?

About deleting/editing a file/folder i managed to delete the examples folder using Kulgan example(thanks also for explaining how to edit a file/folder). As i came from windows im use to a gui and would prefer to use one when possible i.e. the less terminal the better. Is there not a way to make ubuntu ask me for my password when deleting/editing a file/folder this way i wont have to use terminal and its still as secure is it not?

The last.fm folder and is now hidden and my home folder all tidy again :-).  

Also thanks aznboi for the suggested firefox extension its not currently compatible with 2.0 rc3 but ill check it out after 2.0 final comes out.

Thanks

---

### Post by CupofDice on 2006-10-23
Wipe is a terminal program, though there may be a gui frontend somewhere. It automatically uses Gutmann's method.
```

wipe -r /home/user/Foldertobewiped (make sure to use -r when deleting folders)
wipe /home/user/filetobewiped
wipe ~/filetobewiped
[COLOR="Red"]If you are deleting a file/folder in your user directory which you do not have the permissions for or some file/folder in another area which you also don't have permissions (like root itself), use the sudo command.[/COLOR]
sudo wipe /filetobewiped
sudo wipe -r /foldertobewiped
[COLOR="Red"]Be very careful using sudo wipe.[/COLOR]

```

One thing you may want to do when dealing with folders/files in your user directory is delete them the normal way. This places them in /home/user/.Trash . Then wipe .Trash-
```

[COLOR="Red"]In user directory-[/COLOR]
wipe -r .Trash
[COLOR="Red"]Then remake the .Trash folder (it seems to do this automatically either way)[/COLOR]
mkdir .Trash

```
Check my howto if you want to wipe free space and file slacks.
[http://ubuntuforums.org/showthread.php?t=281480&highlight=Bcwipe]("http://ubuntuforums.org/showthread.php?t=281480&highlight=Bcwipe")
Use all of that at your own risk of course. 

I came across some nautilus extension a few days ago that allows you to open a folder with root privilege through the right click 
[COLOR="Blue"]quick search-[/COLOR]
and it may be nautilus scripts in the automatix package.
[http://www.getautomatix.com/wiki/index.php?title=Software_and_Tweaks]("http://www.getautomatix.com/wiki/index.php?title=Software_and_Tweaks")
Probably not a wise idea to use automatix though.
[http://gnomefiles.org/app.php/Nautilus_Scripts_for_Subversion]("http://gnomefiles.org/app.php/Nautilus_Scripts_for_Subversion")
Alright this may be it, but I never been at that site before so be careful.
There is also this.
[http://gnomefiles.org/app.php/GnomeSu]("http://gnomefiles.org/app.php/GnomeSu")

Hope that helps :D and use at your own risk of course.

---

### Post by Ben Sprinkle on 2006-10-23
3 & 4:
```

sudo rm -r '/pathtofolder'

```
For deleting a single file:
```

sudo rm '/pathtofile'

```
Same for deleting the example folder. :)

---

### Post by maaronB on 2006-10-23
I don't know how secure it is.  But if you just want to quickly delete files without moving them to the trash.  Open the file browser.  Click Edit -> Preferances -> Behaviour -> Then check the box marked include delete.

As for being able to delete files that are owned by root(like Examples) without using the CommandLine; one way is to download Automatix2.  It includes a script called Nautilus Scripts (I believe) that enables you to right click on a file and become the root user.  But I have to say that I don't recommend that you use it.  It is very unsecure, wouldn't be used as much as you think, and you should learn the basics of the commandline anyway.  At least things such as sudo, rm , mv, cp, and ls.

---

### Post by Ben Sprinkle on 2006-10-23
Or just do a root login. >.>

---

### Post by CatKiller on 2006-10-23
> **englishmen said:**
> Concerning my first question, i wasnt aware that using Places -> Recent Documents -> Clear Recent Documents: also cleaned programs mru lists as well. I tested it and it does for some but not for others and as i don't know how to write a scrip i guess it will do.

As a slightly-educated stab in the dark, I'd suggest that it's GTK applications - those that are well-integrated with GNOME - that will work nicely. With others, it's at the whim of the developers. Most applications have an option in the Preferences to clear the list though, if there's a particular one that isn't well-behaved that you'd like to clear.

---

### Post by n0dl on 2006-10-23
1.) Open up synaptic by locating it in the gnome panel or opening up a terminal and typing
```
sudo synaptic
```
2, 3, 4.) Open up a terminal cd into the "directory" the file is in (such as Desktop or whatever). Type pwd to make sure your in the correct "directory"
ls to see the file you want to delete is there then 
```
rm -rf filename 
```
or
```
 sudo rm -rf filename
```

---

