---
title: "Some form of shell script?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Javawag on 2008-01-14
Hi all,

I'm new to making scripts for Linux. How would I make a script which issues command line commands (i.e. like a Windows .bat Batch file)? I need a script to unmount a volume, run vmware, and when vmware closes, remount the volume... something like this:

sudo umount /windows
sudo /usr/bin/vmware /home/joe/windows.vmx
sudo mount /dev/hda2 /windows

What kind of file do I need to store that in, and does it need something at the start of it, i.e something beginning with "#!"?

Thanks!
- Javawag

---

### Post by jordanmthomas on 2008-01-14
Technically, it doesn't _need_ the #! at the start, but it's common practice so you can just make the script executable and not have to worry about what to run it with.

```
#!/bin/bash
umount /windows
/usr/bin/vmware /home/joe/windows.vmx
mount /dev/hda2 /windows

```
save this as myscript in your home folder, for example.  Neither the name of the file nor its extension matter.
Then, make it executable:
```
chmod +x ~/myscript
```
Now, you can run it with
```
sudo ~/myscript
```
I would recommed linking it to somewhere in your path as well:
```
sudo ln -s ~/mysrcript /usr/local/bin/myscript
```
and you can just run
```
sudo myscript
```

---

### Post by Javawag on 2008-01-14
Ahh thanks! That's pretty much what I tried although I didn't set it as executable... schoolboy error!! Ok, I'm not sure I need to link it really in this case, as I'm just going to have a shortcut on the desktop for it (what's that called in Linux... symlink?...I'm sorry I can't get out of the habit of using Windows terms!). I might link in future though so thanks for that info too.

Thanks!!
- Javawag

---

### Post by jordanmthomas on 2008-01-14
If you want it to work with double clicking an icon, be sure to change your command from sudo myscript to
```
gksudo myscript
```
so it will ask your password and work properly.

---

### Post by Javawag on 2008-01-14
Thanks for the heads up.

So just to check for certain (cause I'm still quite new to this):

**su** - elevate privileges to *root* - asks _root_ password
**sudo** - elevate privileges to *root* for this command - asks _user_ password
**gksudo** - as **sudo**, but for use in graphical situations rather than command line

Is that right?

- Javawag

---

### Post by bodhi.zazen on 2008-01-14
yes, except su will not work in Ubuntu unless you set a root password.

sudo -i will give you a root shell.

sudo <command> = single command

gksu = use for graphical apps

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by stchman on 2008-01-14
> **Javawag said:**
> Hi all,

I'm new to making scripts for Linux. How would I make a script which issues command line commands (i.e. like a Windows .bat Batch file)? I need a script to unmount a volume, run vmware, and when vmware closes, remount the volume... something like this:

sudo umount /windows
sudo /usr/bin/vmware /home/joe/windows.vmx
sudo mount /dev/hda2 /windows

What kind of file do I need to store that in, and does it need something at the start of it, i.e something beginning with "#!"?

Thanks!
- Javawag

The #!/bin/bash or sh or csh is just denoting which shell to run the script in.  After the first line then start typing commands in the script.  You must them make the script executable.

---

