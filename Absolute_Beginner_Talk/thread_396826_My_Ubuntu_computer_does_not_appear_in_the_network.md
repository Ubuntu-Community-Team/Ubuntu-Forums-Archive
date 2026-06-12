---
title: "My Ubuntu computer does not appear in the network"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by doctorj on 2007-03-29
I am rather new to Ubuntu. I have just installed my desktop computer with Ubuntu. I have installed Samba and can see my other three computers on the Windows Network. On my other computers, however, they cannot see, and do now show the Ubuntu computer as being part of the network. How do I get the Ubuntu computer to show as part of the network?

---

### Post by cowlip on 2007-03-29
Make sure you are in the same workgroup as your other Windows computers by going to System->Administration->Shared Folders, and clicking "General Windows Sharing".  You may also have to set the domain in System->Administration->Networking as your Windows workgroup.

Then, you'll have to create a samba username and password by typing 'smbpassword -a USERNAMEGOESHERE' to login to your Ubuntu shares.

---

### Post by halitech on 2007-03-29
also, have you actually shared any folders on your Ubuntu box?

---

### Post by doctorj on 2007-03-29
OK. I made sure that MSHOME is the domain name in Network Settings, and I have typed in MSHOME in Shared Folders General Properties and I have shared a folder.

I do not know where you are asking me to type in 'smbpassword -a USERNAMEGOESHERE'

Is this to be typed into a terminal? If so, I tried that and got a "Command not found'

---

### Post by halitech on 2007-03-29
it would be in the terminal but I think it's 

[code]
smbpasswd -a USERNAMEGOES HERE
[/code

then enter the password

---

### Post by doctorj on 2007-03-29
Tried the [code] sequence, and still get 'command not found'

---

### Post by david_kt on 2007-03-29
> **doctorj said:**
> How do I get the Ubuntu computer to show as part of the network?

Follow this tutorial:

[http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain](http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain)

DK

---

### Post by JAPrufrock on 2007-03-29
There's an excellent thread in the forum about [Samba peer to peer]("http://209.85.165.104/search?q=cache:VB43pQLBbacJ:ubuntuforums.org/showthread.php%3Ft%3D202605+samba+how-to+ubuntu&hl=en&ct=clnk&cd=3").

---

### Post by doctorj on 2007-03-29
OK. Very helpful. I now see the Ubuntu computer on the Network on all other machines as well as on the Ubuntu machine.

BUT

I am asked for a password when clicking onto the Ubuntu machine. I have tried the password that I thought I added in all the activity. Password and username do not work. Where do I go to make a change or make sure that the Username and Password are correct?

---

### Post by h0ax on 2007-03-30
Just do what they said before
```

smbpasswd -a username

```

---

### Post by cowlip on 2007-03-30
you also might have to restart Samba

sudo /etc/init.d/samba restart

---

### Post by doctorj on 2007-03-30
Well thanks all.

I now have the network running. It is a great effort to do all this to get the network running. But everyone has been good in pointing me to the right source.

Thanks.
:guitar:

---

### Post by cowlip on 2007-03-30
Ubuntu should make this easier and with a GUI way (distros like Red Hat and Fedora already do with system-config-samba or redhat-config-samba)--however, I'm glad you got it working :)

In fact you could probably install system-config-samba onto Ubuntu in a similar way to this, you just have to download (google) and convert the RPM file.  [http://ubuntuforums.org/showthread.php?t=216117](http://ubuntuforums.org/showthread.php?t=216117)

---

