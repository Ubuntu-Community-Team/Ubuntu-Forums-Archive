---
title: "[SOLVED] NFS vs Guarddog Rematch"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-10-11
This is the old story of NFS and Guarddog with perhaps a new twist.

Setup: two machines connected by crossover cable to their respective eth1's to form a LAN. There is no problem sharing files between Windows sessions, or Windows-Ubuntu sessions.

For Ubuntu-Ubuntu, the Server has the NFS export set using the GUI of System > Administration > Shared Folders. The Client is given a new fstab line, '192.168.0.1:/home/files/o/Thorax /home/files/o/Thorax nfs'.

The common advice is that NFS uses random ports, so you must now tie various applications to specific ports, and then add firewall rules to allow those applications to use those ports.

... But then **why** does Guarddog have NFS listed? Just like it lists SMB, which works. Seriously, what's the answer to that? I've been trying to find out for a long time now.

Checking-off NFS in Guarddog does indeed do nothing. Neither does including Sun RPC.

For kicks, I've now checked-off all the protocols in the File Transfer, Interactive Sessions, and Network sections of Guarddog. (Excluding Local-Internet of course. Strictly Local and LAN.)

The first time I did that, it worked. Until I rebooted. I've rebooted several times since. Once, and only once, the file share has worked for the Client machine after a reboot.

What's going on?

----

Further kicks: SMB mostly works okay for Ubuntu-Ubuntu. 

I say 'mostly' because when I enter 'smb://192.168.0.1/' in Konqueror, I am rewarded with being shown the Thorax folder. Then I click it and get 'Error - The file or folder smb://192.168.0.1/Thorax does not exist.'

*... and then the NFS mount point '/home/o/file/Thorax' starts working.*

SMB in the other direction, which has no NFS involvement, works fine.

---

### Post by ofb on 2007-10-12
Minor update - forget that business about the NFS mount point working after getting the SMB failure. They're not related. That was just one of NFS's random working moments.

The smb.conf on these two machines don't match at all. I'll look into that tonight or this weekend - I need to remember what I did to set up the working SMB back in Februrary.

But the NFS questions remain. What is the NFS setting in Guarddog for? And why does NFS work sporatically? I'm entirely stuck there.

---

### Post by ofb on 2007-11-15
Just an update to solve things for people who search the forums.

The above trouble was with 7.04 and an earlier version of Guarddog. SMB and NFS work with 7.10 and its version of Guarddog.[1]

To set up SMB just use the Shared Folders GUI. You no longer need to edit configuration files, or run any refresh commands in terminal.

To set up Guarddog, use its well-written online documenation. The protocol you wish to enable for SMB is under Network, and is helpfully called 'Microsoft SMB Over TCP'.[2]

SMB should work fine at this point. If you are getting 'permission denied' errors, then check that you have correct permissions set for the shared folder in your file manager - the Shared Folders GUI setting cannot override this. Also check premissions of all the directories above the share, so the filepath to it is not blocked.

NFS is not as far out of the Dark Ages yet, so you will need to edit some files and run some CLI commands, though it's not as bad as it used to be. First use the Shared Folders GUI again to create your NFS shares. Create mountpoints for these shares on the opposing machines. Now edit the fstabs to include the shares and their mountpoints. 

In Guarddog enable 'Network File System - Sun Microsystems' for the appropriate zones under File Transfer. Now reboot both machines.[3]

NFS should now work, but it's not entirely automatic.

Remember that on this setup both machines are clients and servers -- both have NFS shares for the other machine to use. Whichever machine is booted first will not be able to see the NFS share on the second, because it wasn't out there when the first's fstab was run. So you need to run the first's fstab again, with 'sudo mount -a'.

Which is all good until you shut off one of the machines, and suddenly the file manager GUIs (Nautilus, Knoqueror, GQView, etc) on the remaining machine jam because of the missing share.

To clear this you run 'sudo umount.nfs [mountpoint] -f'. The '-f' is to force the unmounting. And this doesn't work. It cannot work until you go back into the fstabs and add the option 'hard,intr' to the NFS lines. That allows the unmounting to interrupt resouces that were accessing the share, and now the forced unmount can successfully un-jam your GUIs.

You will still get an error saying the umount.nfs didn't work, even though it appeared to. That's because you cannot actually unmount a volume mounted by the fstab. So you get that error, but for practical purposes you got what you wanted.

All of which could be swept under the rug of the GUIs, as it is with SMB, but that hasn't been done yet. So for NFS you'll have to do a minor portion of the configuration by hand, and you'll have to remember two CLI commands.


Notes

[1] Firestarter still cannot be used with this particular LAN setup. It appears that Firestarter does not enable a second NIC unless you choose to use ICS. Firestarter will confuse you by showing the second NIC assigned to the LAN regardless, but it does not allow traffic through that card, and will continue to refuse no matter what extra rules you add.

[2] My setup also has NETBIOS enabled because I also share with Windows, but I'm pretty sure you don't need that with pure Linux SMB.

[3] Why reboot both machines? I'm not sure. You can refresh the fstabs with 'sudo mount -a' and everything nearly works. However checking the logs indicate the NFS request is received by the serving machine, but then the server is blocked from replying by its own firewall that had allowed the incoming request. That's odd and you're welcome to figure it out on your own time. Meanwhile you can just reboot both and put that problem permanently behind you.

---

