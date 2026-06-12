---
title: "[SOLVED] mounted folders unmount themself"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by runris on 2008-01-06
okay.. thing is I have one huge /data partition I've made to store movies n music and stuff whenever I feel for reinstalling the OS. I mount it in my /home folder using 
"mount --bind" and everything seems fine, but when I reboot it unmounts itself.

so question is. how do I mount a folder (ex. /data/Music) into another (ex. /home/me/Music) and make it stay there after a reboot?

---

### Post by philinux on 2008-01-06
Why not just use a symbolic link from your home folder?

---

### Post by runris on 2008-01-06
> **philinux said:**
> Why not just use a symbolic link from your home folder?

will it work the same way as if I mount the folder in there? how is it done?

---

### Post by philinux on 2008-01-06
[https://help.ubuntu.com/7.10/user-guide/C/gosnautilus-8.html](https://help.ubuntu.com/7.10/user-guide/C/gosnautilus-8.html)

Scroll down half way to create symbolic links.

Or use firefox find - symbolic

> Creating a Symbolic Link to a File or Folder

A symbolic link is a special type of file that points to another file or folder. When you perform an action on a symbolic link, the action is performed on the file or folder to which the symbolic link points. However, when you delete a symbolic link, you delete the link file, not the file to which the symbolic link points.

To create a symbolic link to a file or folder, select the file or folder to which you want to create a link. Choose Edit &#8594; Make Link. A link to the file or folder is added to the current folder.

Alternatively, grab the item to which you want to create a link, then press-and-hold Ctrl+Shift. Drag the item to the location where you want to place the link.

By default, the file manager adds an emblem to symbolic links.
[Note] 	

The permissions of a symbolic link are determined by the file or folder to which a symbolic link points.
[Tip] 	

For more on dragging items, see the section called “Drag-and-Drop in the File Manager”.


Its just basically a short cut like in windows having mydocuments on your desktop.

No need to mount anything then.

---

### Post by dcstar on 2008-01-06
> **runris said:**
> okay.. thing is I have one huge /data partition I've made to store movies n music and stuff whenever I feel for reinstalling the OS. I mount it in my /home folder using 
"mount --bind" and everything seems fine, but when I reboot it unmounts itself.

so question is. how do I mount a folder (ex. /data/Music) into another (ex. /home/me/Music) and make it stay there after a reboot?

Install the** pysdm** package, and then System-Administration-Storage Device Manager, it will set up the required fstab entry for you.

---

### Post by runris on 2008-01-07
philinux: a link don't seem to be the thing here.. I want to be able to use the Places-menu to easy access my Music and Videos-folders. And I have a ton of subfolders in my /data/Music, so linking all of them don't sound like an easy way to solve it.

dcstar (or anyone who knows how it's done): I've installed pysdm, but I'm not sure what to do in it.. think you could write down a little step-by-step list for me?

---

### Post by runris on 2008-01-07
SOLVED!

added the command in fstab followed by "none bind".

---

