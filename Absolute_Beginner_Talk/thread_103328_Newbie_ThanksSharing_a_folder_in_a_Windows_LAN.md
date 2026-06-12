---
title: "Newbie Thanks/Sharing a folder in a Windows LAN"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by randbag on 2005-12-13
I'm one week new to Linux and just set up my first machine using Ubuntu. I've learned a lot from this forum and want to thank everyone who's contributed.

I'm in a classroom in a large school district and needed a way to share folders securely and without wasting valuable computing resources. (As a lowly teacher, I am not allowed any access to any of the servers. And as an experienced teacher, I want sometimes to control the share folder.) What I finally did was install Ubuntu on a cranky old Compaq and then create a share folder for my students who use a mix of Win98 and WinXP computers. 

While toiling with this, I found a lot of instructions that left out something a newbie like me really needed to know, so I put it all together in one place, borrowing from others in this forum. Ubuntu/Linux veterans, please correct anything I have wrong. Here it is:

**STEP 1: Set up the user(s) who will access the share folder.**

1. In Ubuntu, click on:**  System, Administration, Users and Groups**.
2. In the Users and Groups window, add the username(s) of the person(s) who will access the share folder. 
3. Decide which password to give to that user and enter it twice; it won't affect the password the user will need to access the folder, as you will set that later. (I decided not to share that password with the user group that includes my students so I could better control the share folder.)
4. Click **OK**.

**STEP 2: Set up the Share Folder**

1. Create/decide which folder to share.
2. Right-mouse click that folder and click on: **Share folder**
3. In the Share Folder window, select: **Share with: SMB**
4. Check: **Allow Browsing Folder**
5. Click: **General Windows Sharing Settings**
6. Fill in the** [B]Host Description** box
7. Fill in the **domain/workgroup **box with the name of your domain or workgroup
8. Click **OK**
9. Right-mouse click the share folder again and click on: **Properties**
10. Click on the **Permissions **tab
11. In the **Others **row, make sure to check all of the boxes: **read, write, execute**

**STEP 3: Set up Samba**

*Note: To use these instructions in Ubuntu, click on Applications then Accessories then Terminal to open the command terminal.*

1. Set up/install Samba with the following command: **sudo apt-get install samba**
2. Once the server is installed, issue the following command: **sudo gedit /etc/samba/smb.conf**
(This will open a text editor)
3. Make the following changes in the file: **workgroup = WORKGROUP** 
(insert the name of your workgroup or domain in place of **WORKGROUP**)
4. Underneath it, add: 	**netbios name = name_of_your_server** (no spaces)    
For example: **netbios name = kenny_smb_server**
Another example: **netbios name = yearlyreview**
5. Make sure **security **is set to **user**. 
6. Scroll down until you see "[homes]" and set:	**browseable = yes **
and **writable = yes**
7. Save the changes and close the text editor.
8. Create a samba user. The code for this is: **sudo smbpasswd -a `whoami`**
An example is: **sudo smbpasswd -a 'susan'**
9. Set that user's password when prompted; it can be different from the one set earlier for the computer.
10. Restart Samba for this to take effect: **sudo /etc/init.d/samba restart **
11. Close the terminal editor.

You're now ready to access that shared folder from a Windows computer. 
When in a Windows computer, **browse network neighborhood**/**network places**. You may need to click on **Entire Network** and navigate to the workgroup/domain. When there, look for the name you gave earlier to the Ubuntu computer and share folder. You may wish also to right mouse click the Ubuntu share folder when you find it and map it to a drive. The first time you access the folder, you'll need to provide the password you created earlier. If you choose for your Windows computer to remember the password, you won't need to enter it any more.

That's it. Forum contributors please let me know if I made errors here. I'll try to compile them all and repost a corrected process. Thanks again.

---

### Post by prince_niceguy on 2006-11-06
Thanks randbag!!!

Your tip on the creation of the user was the one which I needed. This made it possible for me to access my linux box from windows system...

thanks so much...

---

### Post by gagan_mishra on 2006-11-11
is it possible to browse the LAN through terminal?
the command 'smbfind' shows the unix abd windows machines on my LAN, is it possible to browse through the PCs and the shared contents through the terminal using command lines ?

---

### Post by Sef on 2006-11-11
Thanks for tutorial.  I am sure others will benefit.

---

### Post by perlmonger on 2007-04-07
The education system in the US needs more teachers like you. This is an excellent tutorial on sharing samba shares on a windows network. I've been trying (sorta) for a while to get this to work. I've just been too lazy to dig through the docs to figure it out. Thanks again for sharing your experience with others.

---

### Post by kc5hwb on 2007-04-07
Good info.  I just did this setup myself.  Except that I have more than 1 Ubuntu box on my Windows LAN, so it a made it kinda tricky to share folders between 2 Linux boxes with Samba.  I don't wanna hijack this thread, so I am not posting my steps here, but if you wanna read how to do it, here is a link:
[http://forums.keyboardjunkies.com/index.php/topic,1218.0.html](http://forums.keyboardjunkies.com/index.php/topic,1218.0.html)

---

### Post by nwadams on 2007-06-27
is it possible to make it so i do not need a user to log in, perhaps set the security to a setting that allows all to see

and how can i print from ubuntu to a printer attached to a windows computer

---

### Post by fherescobar on 2007-08-26
I couldn't get it done... I mean, i see the workgroup from windows but when I try to access it, it won't let me, telling me that i got no permissions to enter.
Anyone plz help!

---

### Post by OttifantSir on 2007-08-28
> **nwadams said:**
> and how can i print from ubuntu to a printer attached to a windows computer

I haven't yet been able to verify that it works myself as I have no toner in my printer, but one way that seemed to work was to simply: 

1. Go to Printers under System>Administration. Click "Add New" or "New Printer" (working in Norwegian, any one of these may be the right, or both wrong, but NEW is probably in there somewhere;))

2. In the window that comes up, mark Network Printer.

3. Choose the protocol that pertains to you. Myself I needed to use SMB or Samba, as I have the printer connected to a Windows machine.

4. Insert hostname (or possibly IP-adress will work if you have a static-IP network, I haven't checked it out, it just seems it should be working)

5. Insert name for printer (If you haven't already installed the printer locally, don't bother with this yet)

6. Insert username and password for Windows-logon (I guess. I'm a newb)

7. Hit Forward/Next

8. Choose your printer (If not listed, choose the closest one, or search around for a driver for your specific printer if it doesn't work for you)

9. Hit Forward/Next

10. Give the printer a name

11. A short description

12. And its location. (These last three aren't really necessary I guess, just info to yourself)

That's how SMB gets printjobs done. "IPP/CUPS", "UNIX (LPD)" or "TCP/Socket, HP JetDirect, RAW connection" is beyond my abilities for the time being.

---

