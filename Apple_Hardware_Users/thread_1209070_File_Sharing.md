---
title: "File Sharing"
date: 2009-07-09
forum: Apple Hardware Users
---

### Post by Evildemon989 on 2009-07-09
Well, before in 8.10 I used to use samba to setup file sharing on so my mac could see my ubuntu machine in the Network tab in finder. This is what I would do:

> How To Make a Samba AFP File Sharing Server On Ubuntu

1. Run these two commands in Terminal:

	&#8226;	sudo aptitude install samba
	&#8226;	sudo nano /etc/samba/smb.conf

2. In the smb.conf file, scroll down to "Share Definitions" and you should see a "comment = Home Directories" parameter. Under that, change the "browsable" parameter to yes.

3. Change the read only parameter for home directories to no.

4. Scroll down a little bit more until you get to "comment = User Profiles". Change the "guest ok" parameter to yes, and the "browsable" parameter to yes.

5. Now press Ctrl+X. Then press Y when it asks you to save. Then press Enter if you are still on the smb.conf page.

6. Now run this command:

	&#8226;	$ sudo smbpasswd -a

Enter when prompted. The user should be added now.

7. Now start samba:

	&#8226;	sudo /etc/init.d/samba start

8. Then, make it run the daemons at boot time:

	&#8226;	sudo update-rc.d samba defaults

9. Now, go into the File Browser, and navigate to the user folder. Right click the all of the folders inside that folder(one by one), and click on "Sharing Options" each time. Then, check "Share This Folder" and check "Allow other people to write in this folder". Finish by clicking "Modify Share".

10. Then, restart Ubuntu, and relaunch Finder after Ubuntu starts up. Go to the "Shared" section in finder, and "-desktop" should show up. Click it and connect as the Ubuntu user. Make sure to check "Remember This In Keychain".

11. You should now be able to write to every folder in Ubuntu from OSX.

But I just installed 9.04 and I'm now running into a problem. When I try to do "sudo aptitude install samba" it says it can't find a candidate version. I need to know how I can get this to work so I can see my ubuntu box in finder. Thanks.

---

### Post by pytheas22 on 2009-07-09
"sudo aptitude install samba" works for me on Ubuntu 9.04.  Try updating your sources list; it may help:
```

sudo apt-get update
```

If that doesn't solve the problem, please post the output of:
```

cat /etc/apt/sources.list
```

---

### Post by Evildemon989 on 2009-07-10
> **pytheas22 said:**
> "sudo aptitude install samba" works for me on Ubuntu 9.04.  Try updating your sources list; it may help:
```

sudo apt-get update
```

If that doesn't solve the problem, please post the output of:
```

cat /etc/apt/sources.list
```

Ah, I updated the sources list and I did "sudo aptitude install samba" again, and it worked. Thanks for your help.

HG

---

### Post by Evildemon989 on 2009-07-10
Well, after that, I got it to show up in finder, and it shows all of my username folders. But, it won't let me drag anything from my mac over to say the desktop. I followed the same guide as the one I posted. If anyone can help me, it would be greatly appreciated.

---

### Post by pytheas22 on 2009-07-11
Do you mean you can't copy from the samba folder to the desktop on your Mac, or on your Ubuntu computer, or both?  Is there any error message?  Does the file share seem to work alright otherwise--for example, can you see all the files and open them remotely?

---

### Post by Evildemon989 on 2009-07-11
> **pytheas22 said:**
> Do you mean you can't copy from the samba folder to the desktop on your Mac, or on your Ubuntu computer, or both?  Is there any error message?  Does the file share seem to work alright otherwise--for example, can you see all the files and open them remotely?

Well, even before I installed samba, I could connect up to my mac from my ubuntu box by going to Places>Connect to Server.

But this is a problem that I can only read from my mac, not write. So I'll try to copy over a file to my ubuntu desktop from my mac, and it will not work.

**Edit: Nevermind. It works, it just for some reason wouldn't copy over a .rpm file. Thanks guys.**

---

