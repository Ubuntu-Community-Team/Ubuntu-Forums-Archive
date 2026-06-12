---
title: "SAMBA Setup"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by Linuxmyatuk on 2006-01-08
HEllo.
I believe I have installed SAMBA on my 5.10 machine.. I figured I would have an admin interface panel under either Applications or System. It is in neither.  looking to do some file sharing between a couple of my home PC's in my network.

One problem I have is that from my windows XP machine I can see my Ubuntu box but it is under a different Workgroup..   How do I change the workgroup in Ubuntu to match the workgroup my network is on and second where can I find an Admin Interface panel?

Thanks in Advance

---

### Post by tabinin on 2006-01-08
You can edit /etc/samba/smb.conf file directly with

```
sudo gedit /etc/samba/smb.conf
```

or use something like Webmin with the samba module to make these changes via a GUI.

---

### Post by matiastepli on 2006-01-08
SWAT is another alternative to configure Samba in a graphical way (using firefox).

Once you edit the /etc/samba/smb.conf with gedit, you will find almost on top a line like this:

```

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = workgroup_name

```

Just change the workgroup value with the name you want.

Regards!.

---

### Post by Linuxmyatuk on 2006-01-08
Under the Work group name.. The correct work gorup name is there.  why would it be under a different work group name in windows..  Windows is now showing that I have two work group names.  The one I created "NETWORK" and the default "MSHOME"  Ubuntu is showing in windows under the default work group but is listed on the Unbuntu machine as NETWORK..

How might I go about getting SWAT?

---

### Post by AndyCooll on 2006-01-08
Try rebooting your Windoze pc, it'll give the networking system a fresh start. Hopefully your Linux box will show correctly this time.

:cool:

---

### Post by dus10 on 2006-01-09
I can see my ubuntu machine from my windows pc but it ask for a username and password.  I put in my username and password that I use to login to the ubuntu machine but I cant access the location that I set up as a samba share; it gives an error.  How do I access that share now?

---

### Post by ptmurphy on 2006-01-09
[QUOTE=dus10]I can see my ubuntu machine from my windows pc but it ask for a username and password.  I put in my username and password that I use to login to the ubuntu machine but I cant access the location that I set up as a samba share; it gives an error.  How do I access that share now?[/QUOTE]


You need to set a samba password for the user.  The user must be a valid linux account (the one you login with is fine), but it is a separate password.

Use smbpasswd -a username password

Then try it from the windows box.

---

### Post by sabredog on 2006-01-10
I have a similar issue.

I set up Samba on my Breezy PC but cannot see the PC via the other XP PC's on the network. Breezy can see the XP PC's though, without issue.

I will try the reboot option and see how that goes!

---

