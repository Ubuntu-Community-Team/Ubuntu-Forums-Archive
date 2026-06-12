---
title: "Gfcon"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by dwdude on 2007-07-21
No idea what's going on... Everytime I try clicking on any file to open an application (or almost anything at all) I get an error. This is what it says:


GConf error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: IOR file '/tmp/gconfd-david/lock/ior' not opened successfully, no gconfd located: Permission denied 2: IOR file '/tmp/gconfd-david/lock/ior' not opened successfully, no gconfd located: Permission denied)

I can still like, view pictures and things like that, but anything that requires permission doesn't work. The Terminal doesn't really work either. I try loading that up and this is what it says:


bash: /dev/null: Permission denied
bash: /dev/null: Permission denied
bash: /dev/null: Permission denied
bash: /dev/null: Permission denied
bash: /dev/null: Permission denied
bash: /dev/null: Permission denied
bash: /dev/null: Permission denied
bash: /dev/null: Permission denied
bash: /dev/null: Permission denied

And it continues saying that, filling the Terminal screen with that.

I am on Feisty and this is getting kind of annoying... Also, when I open file broswer, just to browse around the folders, It doesn't show the full screen. Kind of hard to explain. It just shows the white background with the folders showing (as icons) It shows the File, Edit, View, ect. and at the bottom, it shows like, when you select a file or folder, shows the name and it's size in parenthesis.

Any help would be great!!

Thanks guys :)


EDIT: Lol, spelled the title of the post wrong... Gconf is what it should be named.

---

### Post by dwdude on 2007-07-21
Ok, I got my account working. But not root.
I went into File Browser, browsed to /tmp/gconfd-david/lock and found the ior file. I right clicked it, clicked Properties. Then i Clicked the permissions tab and under Owner:david, next to Access, I made it Read only. Then I clicked close and reopened File Browser. 

I don't get that error unless I try doing something that needs permission (like the terminal or moving folders in the file system)

Terminal displays the same error. No commands work either. No matter what I type. It's almost as if opening Text editor. Type something and hit Enter, it just goes to the next line. Doesn't actually do anything.

If you need anymore info, I'll try my best to get it. Not very experienced.

EDIT: 1) Didn't mean to double post, meant to edit the first one. 2) When I browsed to the folder in /tmp/gconfd-root, there wasn't anything in there. Any Ideas?

---

### Post by dwdude on 2007-07-21
Ok. We just had a power surge and the computer turned off.

Firefox doesn't open. When I click on it, a popup named "Alert" comes up, but there is no message... There isn't even an "Ok" or "Cancel" or anything. So I close that.

Then, I try to add or remove things from Applications>Add/Remove and nothing ever starts. It just refreshes the list again.

Terminal works now, but if i try using sudo, I believe it says something like "etc/sudoers has 0660, not 0440" or something like that.

Also, when i logged in at the start screen, before it showed the desktop, it showed a message saying something like " Home/user/.drmc is being ignored, which means the default language and settings won't apply"

Neither of those messages are exact, because I am using a Ubuntu live cd.

If you really need the exact messages, I'll log back in.

Help please? I really don't want to have to reinstall Ubuntu... Or Windows for that matter.

---

### Post by dwdude on 2007-07-31
I just reinstalled Ubuntu.

Works now... :|

---

