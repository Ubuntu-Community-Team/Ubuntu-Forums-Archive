---
title: "Samba Help"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by cloudydaysbehind on 2005-06-27
I'm trying to see if I can run linux in a windows environment.  At work, all the PCs and servers are windows.

I tried using samba at home to connect to my networked NTFS drives.  When I try to save a file, it won't let me.

Here are the permissions:
ls -l /media
--------------
drwxrwxrwx 1 root root 4096

mount | grep
--------------
smbfs (rw)

Some say that Linux can't write to NTFS, even networked.  Some say Samba should be able to write to a networked drive.

1.  What is correct?
2.  If Samba can write to networked drives, how can I make it so it does?

Thanks for the help!

---

### Post by intangible on 2005-06-27
Make sure you allow write access on the share on Windows Server.

Samba will allow linux to write to NTFS over the network, I do it here often.

Look in the Event Viewer on the Windows box and find out what username it thinks is trying to write to said directory and failing.

---

### Post by cloudydaysbehind on 2005-06-27
Not being able to save to the networked drive happened on my home PC.  I think it might be because I don't have the "allow users to change me files" box checked in XP.  

At work, when I try to mount a drive, it tells me access denied.  I can run smb://server/drive and I get access to the drive, and I was able to make a new folder and copy a file there (so I know I CAN read/write our networked drives.

Now I need to know why I can't mount a networked drive.

9594: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
is what I get when I type
root@beaker:/home/stephen # mount //drive/share /media/share -o username=user,password=password,dmask=777,fmask=777

and 
9718: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
when I type the mount command without my username and password.

I am on a domain, and I tried domain/user, but it didn't work either.  The SMB protocol allowed me to enter the domain.  Does that have any effect on this?

---

### Post by intangible on 2005-06-27
The domain issue could be the problem.  Try adding **winbind separator = +** to your **/etc/samba/smb.conf** and then try using the option **username=DOMAIN+username** in your mount line.

---

### Post by Ken.Lank on 2005-07-19
[QUOTE=intangible]The domain issue could be the problem.  Try adding **winbind separator = +** to your **/etc/samba/smb.conf** and then try using the option **username=DOMAIN+username** in your mount line.[/QUOTE]
 Can the \ be used as the winbind separator?  Normally in windows when specifing domain & passwork it is done as domain\password.  Is there a reason you can't set the winbind separator = \ instead?

---

### Post by intangible on 2005-07-20
Possible, but in unix systems, some apps use \ to "escape" a charactor, so you end up using \\ in some places, and \ in others.

---

### Post by Nequeo on 2005-07-20
One thing worth looking out for that can cause write access errors in Windows XP Professional - (reguardless of what OS is trying to write files to it), is that share permissions are separate  - and take precedence over - file security settings.

Even if the user you are connecting as has write access to the folder, you need to make sure the share is enabled with write access on Windows. In XP Home, or Pro with 'simple file sharing enabled', that means ticking the 'allow users to change my files' box someone already mentioned.

If you aren't using simple file sharing, (if if you're on a Domain you won't be!), just hit the permissions button on the sharing tab. If you tick all the boxes, then all you need to worry about is the user/group permissions under the security tab.

Cheers,

---

