---
title: "Locked Folder"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2006-11-01
Hi,

I have a locked folder. That is, a folder icon with a picture of a padlock next to it. I created the folder myself when I downloaded some .rpm files. The folder is on my desktop. I don't want it, but because of the lock I can't move or delete it and it's making things look messy.

I also noticed, there are fonts folders which I want to get rid of, because I don't want the fonts. But these are also locked with the padlock sign.

Isn't it any oxymoran having a Linux system with locks on?

---

### Post by EriktheUnready on 2006-11-01
it's only a permissions setting.
Right click the folder and tick the "write" block
now you can delete it.
:-D

---

### Post by Tweedicus on 2006-11-01
That didn't work with this folder, the write box was greyed out. I just found a solution though

sudo gknautilus

Then navigate to the location of the folder in question:

/home/tweedicuscomputer/Desktop

Then I can delete it as normal from within nautilus.

Thanks for replying though.

Tweed

---

### Post by azharc on 2006-11-01
Yeah you basically made youself a super user. You can also do that by just typing 'su' in Terminal. (excuse me if I'm wrong, I'm very newb but offering my 2 cents)

---

### Post by Tweedicus on 2006-11-01
So far as I know 'su' doesn't work in Ubuntu, though it does in other deb releases. Try it and see.;)

---

### Post by zgornel on 2006-11-01
try: sudo chown -hR Your_user_name /path/folder

---

