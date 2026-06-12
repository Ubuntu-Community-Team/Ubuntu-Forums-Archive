---
title: "[SOLVED] How do i view a shared folder on a windows network in ubuntu?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by nappymonster on 2008-04-11
I have a network called "Home" consisting, at my house, of about 5 or 6 computers. "Family Desktop" Has a folder in shared docs that i want to copy over to ubuntu, without the hassle of copying it to USB stick. Whenever i go to places>>Network>>Windows Network>>Home
I get the message

'The folder contents could not be displayed
Sorry, couldn't display all the contents of "Windows Network: home".'

Then no computers show up :(


This would REALLY help if i could.
Thanks,
Nappymonster

---

### Post by njparton on 2008-04-11
[LIST]
[*]Make sure both computers have the same workgroup name
[*]Make sure you're using the same username on both computers
[*]Make sure you're using the same password on both computers
[*]Make sure that you've shared the folder in windows correctly and with the correct security settings[/LIST]You should then be able to open it in ubnutu.
 
If you want to use it all the time then you could mount it using cifs, please search this forum for how to do that.

---

### Post by KevinD_Atl on 2008-04-11
[FONT="Arial"]Also check when in the Network browser that you see the "Workgroup".  On mine, I see the "MSHome", which is the generic workgroup for Ubuntu.  The "workgroup" is default for the XP clients, so you may need to just find the workgroup one.

is it XP Pro or Home ?  Do you have simple file and print sharing turned off? Do you have full permissions to everyone to read on that folder share?[/FONT]

---

### Post by david_kt on 2008-04-11
Below is to share from ubuntu to windows, but may be could you to join ubuntu to windows network:

[http://ubuntuforums.org/showthread.php?p=4694652#post4694652](http://ubuntuforums.org/showthread.php?p=4694652#post4694652)

DK

---

### Post by nappymonster on 2008-04-11
File + printer sharing is on.
Same workgroup? What does that mean?
I'm going to create an account called Mark, to access the files. (I realised atm i only have a usb 1 drive; i'm not copying 300mb+ of data to that!)

Nappymonster

---

### Post by quirks on 2008-04-11
Hi, nappymonster!

I have also noticed that automatic discovery of other computers on the network doesn't always work. I couldn't figure out the reason, though.

When Ubuntu does not find your Windows PC, you can connect to it manually. You need the IP address of your Windows computer to do this:

1. On your Windows PC, go to **start -> Run ...** and type **cmd**. A command prompt appears (black window).
2. Type **ipconfig **and press Enter. The command should show you the IP address of your PC (something like **192.168.1.10** or similar).
3. Go to your Ubuntu PC and open the file browser (go to **Places -> Home Folder**).
4. Then, in the address bar type **smb://<IP address of you Windows PC>** (e.g., **smb://192.168.1.10**).
5. Maybe you are prompted for a username, workgroup and password. Enter a username of the Windows computer as well as the appropriate password. As a workgroup, enter the workgroup which the Windows computer belongs to. You can find the workgroup when you right-click **My Computer** in the start menu and select **Properties**.

If everything woks fine, you should see the shares on your Windows PC now. In case you have any trouble following the above steps, don't hesitate to ask!

If it still doesn't work, there could be something wrong with the permission. Again, just ask!

quirks

---

### Post by njparton on 2008-04-11
> **nappymonster said:**
> File + printer sharing is on.
Same workgroup? What does that mean?
I'm going to create an account called Mark, to access the files. (I realised atm i only have a usb 1 drive; i'm not copying 300mb+ of data to that!)
 
Nappymonster
 
Remember that as far as linux is concerned, mark and _M_ark are different (case sensitive).

---

### Post by nappymonster on 2008-04-11
just followed [This Video]("http://www.youtube.com/watch?v=Ad17kma8rNM") and can now copy+paste stuff to ubuntu from windows. I also wanted to do it the other way around, but hey ho, it's now better than USB 1 :D

Nappymonster

EDIT: Posting this just refreshed the page, and thanks to the above 2 posts; they are great! Thread Solved.

---

