---
title: "Copying files"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Eric Weir on 2007-09-17
I am an _absolute_ absolute beginner. Installed Ubuntu less than a week ago. I the process of moving over from Windows 98SE. Many things are intuitive, in addition to the help files on the Ubuntu machine I have a couple of books to help me when they're not -- or when my intuitions are wrong.

I am stuck on something very elementary: copying files. I tried moving my Windows Firefox bookmarks to my Firefox profile on Ubuntu. I copied the Windows bookmarks to a floppy. I backed the Ubuntu bookmarks up to anothe floppy. When inserted the Windows disk in the Ubuntu machine, it recognized the disk but wouldn't display the file. When I replace the Windows disk with the Ubuntu disk, it wouldn't display that file either. I tried copying the Ubuntu bookmarks again and got the "file already exists" warning. So the file is there, but for some reason it's not displaying.

If I can't copy one file, I'm certainly not going to be able to copy my data files from the Windows machine. What am I not being told? Or, what am I overlooking?

Help will be greatly appreciated.

---

### Post by kellemes on 2007-09-17
You wanne leave Windows for ever?
If so.. can you access the Windows-drive from Ubuntu filemanager? (nautilus)
If not.. you can also create an extra partition to share data between the two OS's, I have one sharedisk (formatted ext3) with my firefox-profile and simply point to this profile from Linux and from Windows.

---

### Post by Eric Weir on 2007-09-17
> **kellemes said:**
> You wanne leave Windows for ever?

That's where I'm headed, but I have to do it slowly -- because I have work that needs attention, because I'm learning as I go.

> If so.. can you access the Windows-drive from Ubuntu filemanager? (nautilus) If not.. you can also create an extra partition to share data between the two OS's, I have one sharedisk (formatted ext3) with my firefox-profile and simply point to this profile from Linux and from Windows.

I can't. They're on separate machines, which was why I used a floppy.

Thanks

---

### Post by eapache on 2007-09-17
You say it recognizes the disk, but won't display the file... does the disk show as empty, or as having other files on it? Please be specific.

---

### Post by FuturePilot on 2007-09-17
In Nautilus
View>Show Hidden Files. It's most likely hidden for some reason.

---

### Post by Eric Weir on 2007-09-17
> **eapache said:**
> You say it recognizes the disk, but won't display the file... does the disk show as empty, or as having other files on it? Please be specific.

The disk shows as empty, but when I try copying the file a second time I get the warning "file already exists. copy over?" So it's there, but it doesn't show up. 

Thanks,

---

### Post by aysiu on 2007-09-17
Maybe, for whatever reason, the graphical file manager is having trouble refreshing the view.

Let's try [the terminal.](http://www.psychocats.net/ubuntu/terminal)

Pop the floppy in and then paste this command in the terminal: ```
df -h
``` Then paste the output back here.

---

### Post by luptinpitman on 2007-09-17
Sounds to me like there might be a problem with the way the floppy is formatted.

If it shows up under df -h and it isn't hidden when you try ctrl+h, then I would think about trying a different disk or taking a look at how it is formatted.

---

### Post by Eric Weir on 2007-09-17
> **FuturePilot said:**
> In Nautilus
View>Show Hidden Files. It's most likely hidden for some reason.

Thought I resonded to this earlier, but the response hasn't shown up here. So here goes again:

When I did View>Show Hidden Files, the file showed up. 

Now I've got another problem: Nautilus says, "You don't have permission to copy that file." I logged in the Login Window, but get the same message when I try the copy again.

So, more instruction needed.

Thanks,

---

### Post by Eric Weir on 2007-09-17
> **aysiu said:**
> Maybe, for whatever reason, the graphical file manager is having trouble refreshing the view.

Let's try [the terminal.](http://www.psychocats.net/ubuntu/terminal)

Pop the floppy in and then paste this command in the terminal: ```
df -h
``` Then paste the output back here.

Here's the output: 
[INDENT]Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             9.0G  2.6G  5.9G  31% /
varrun                237M  100K  236M   1% /var/run
varlock               237M     0  237M   0% /var/lock
procbususb            237M   96K  236M   1% /proc/bus/usb
udev                  237M   96K  236M   1% /dev
devshm                237M     0  237M   0% /dev/shm
lrm                   237M   33M  204M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/fd0              1.4M   28K  1.4M   2% /media/floppy0
[/INDENT]

Thanks,

---

### Post by Eric Weir on 2007-09-17
> **luptinpitman said:**
> Sounds to me like there might be a problem with the way the floppy is formatted.

If it shows up under df -h and it isn't hidden when you try ctrl+h, then I would think about trying a different disk or taking a look at how it is formatted.

What kind of formatting is required? The disk was a new one. Formatted for Windows PC. I was under the impression that Ubuntu would read those. Am I mistaken?

Thanks,

---

### Post by aysiu on 2007-09-17
Can you now paste in these commands? ```
cd /media/floppy0
ls -al
``` and then post the output back here?

---

### Post by Eric Weir on 2007-09-17
> **aysiu said:**
> Can you now paste in these commands? ```
cd /media/floppy0
ls -al
``` and then post the output back here?

Here's the output:

[INDENT]total 39
drwxr-xr-x 2 eric eric  7168 1969-12-31 19:00 .
drwxr-xr-x 5 root root  4096 2007-09-17 14:43 ..
-rwxr-xr-x 1 eric eric 27953 2007-04-03 10:52 bookmarks.html
[/INDENT]

Thanks again,

---

### Post by luptinpitman on 2007-09-17
Sorry Eric, I didn't see your earlier response that the file was indeed hidden.

Couple of ways to do it.

If you want to use the GUI, there is a quick and dirty way (take this with a grain of salt because it is most assuredly the wrong way to do it for security purposes).

from a terminal you can type:  sudo nautilus

This will launch nautilus with root permissions and allow you to right click copy/paste all you like.  Not sure if the permissions will follow the file.

Once you copy the file over from the floppy to say your home directory you can then change the permissions to allow you to work with the file.

1.  Copy the file to your home directory.
2.  Open a terminal and type cd ~
3.  Then type sudo chmod 700 filename

This should allow you to then do whatever you want with the file.

---

### Post by aysiu on 2007-09-17
> **Eric Weir said:**
> Here's the output:

[INDENT]total 39
drwxr-xr-x 2 eric eric  7168 1969-12-31 19:00 .
drwxr-xr-x 5 root root  4096 2007-09-17 14:43 ..
-rwxr-xr-x 1 eric eric 27953 2007-04-03 10:52 bookmarks.html
[/INDENT]

Thanks again,
Now try pasting this in: ```
cp /media/floppy0/bookmarks.html ~/Desktop
``` Your bookmarks file should now be on your desktop and ready for import into Firefox.

---

