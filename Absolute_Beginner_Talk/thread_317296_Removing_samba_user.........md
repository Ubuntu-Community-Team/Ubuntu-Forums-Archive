---
title: "Removing samba user........"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by Nhatz on 2006-12-12
how can i remove samba user....? thanks! :confused:

---

### Post by gh0st on 2006-12-12
I'm not an expert on this but I did find this guide, hope it helps you. If you only want to remove a user from the samba server I think you only need to do the first bit. You will need to restart samba after you've done it though I think. This might be the blind leading the blind here so appologies if it doesn't work. You could probably just use the command  "sudo smbpasswd -x <user>". Good luck

------------------------------------------------------
How To Delete Users From Your Samba Domain

Deleting users from your Samba domain is a two stage process in which you have to remove the user from the Linux server and also remove the user's corresponding smbpasswd entry. Here's how:

1. Delete the users using the smbpasswd with the -x switch

[root@bigboy tmp]# smbpasswd -x john
Deleted user john.
[root@bigboy root]#

2. Delete The Linux User by following the normal deletion process. For example, to delete the user john and all john's files from the Linux server use:

[root@bigboy tmp]# userdel -r john

Sometimes you may not want to delete the user's files so that they can be accessed by other users at some other time. In this case you can just deactivate the user's account using the passwd -l username command.

-----------------------------------------------------------------
That info is taken from [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows,_Linux,_and_Samba](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows,_Linux,_and_Samba)

---

