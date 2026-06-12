---
title: "To make Virtual Box shared folder accessible to user in Ubuntu 11.10"
date: 2011-12-08
forum: Apple Hardware Users
---

### Post by graddad on 2011-12-08
I use Virtual Box on my MacBook Pro under OS 10.7.2. I run Ubuntu in VM through Virtual Box. I was frustrated to find that my shared folder in the Linux OS directory [/media/sf_VM_Drop_Box] was not readily accessible. I had no problem setting it up to share in VB. The problem was always on the Linux side. I had to Command-Click the [/media] folder and open as administrator, and then do the same for the Virtual Box sharing folder inside [/media] every time I wanted to access it. 

So I tried every way I could find to make the folder readily accessible. I tried to change permissions with [chmod] and ownership with [chown] without success. Finally I thought if I could add myself to the [vboxsf] group that owned the folder then that would open possibilities. Here is how I did it.

Open Terminal program, login with your username and password if needed. At the command prompt [ ~ $ ] enter the following...

~ $ cd /etc/group

This puts you in the right directory. Press return to enter command, then...

~ $ cat group
&#65279;
Press return. Notice the group near the bottom of the list [vboxsf]. This is the line you will edit.

~ $ sudo usermod -G vboxsf -a [your username]

Reboot, open Terminal...

~ $ cd /etc/group

Press return to enter command, then...

~ $ cat group

Notice that your user name now appears in the [vboxsf] group.

Quit Terminal. Go back to GUI desktop. Open home folder, then open [File System] folder. Go to [/media] folder and select "Open as administrator" by using [Command-Click] or whatever button your mouse uses to get the menu for the item. You will need to enter your password. 

A new folder window should open. This folder window is an administrator folder window. Do not close it until done.  [Command-Click] the Virtual Box shared folder inside. Select the "Sharing Options" menu item and complete the window that opens. Navigate back one level and do the same for the [/media] folder. 

Now navigate back inside the media folder again. [Command-Click] the Virtual Box shared folder and select "Make link." This will appear in the [/media] folder. You can edit the name of the link if you wish. Drag the link to the GUI desktop. Close the folder windows. Reboot. Now using the link the Virtual Box shared folder will open without having to navigate to it and use "Open as administrator."

---

