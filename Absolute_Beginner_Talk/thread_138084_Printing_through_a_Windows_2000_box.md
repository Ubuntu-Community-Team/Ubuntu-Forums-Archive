---
title: "Printing through a Windows 2000 box"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by myotis on 2006-03-01
I have small network using a Vigor router, I have recently replaced WIN2000 with Ubuntu Breezy on on of the boxes.

I am trying to print to a Samsung CLP-500 which is connected to a WIN2000 box, also connected to the Ubuntu box through the router.

I have installed the  Linux driver, and CUPS seems to detect the printer, but trying to send a test print does nothing, just a dialog box saying that it is being printed. Trying to print from OOo has the same problem.

I have read similar questions in teh froum, and searched the web, but I am still not sure what I should be doing to fix this.

Help much appreciated.

Thanks,

Graham

---

### Post by myotis on 2006-03-01
Can I addd to this in that I am now getting an error message in the Samsung property box

Ready Connection failed with error NT_STATUS_LOGON_FAILURE

Graham

---

### Post by Stealth on 2006-03-01
Ok, first make sure you have samba installed:

```
sudo apt-get install samba
```

Then, when you setup up your printer choose the Samba option, in the hostname put in the IP of the Win2K box, then for Printer type in the Printer's name (probably just "Printer") and in username and password put in your Ubuntu username and password...

and of course do the rest by choosing the appropriate printer from the list, and see how that works :)

---

### Post by myotis on 2006-03-01
Thanks,

The command tells me that I have the latest version of Samba installed.

This is what I am doing

I open system|admin|printers

Choose add printer (Global settings are set to detect lan printers)

I then select Network printer and change the option from CUPS to Windows printer (SMB)

A dialog box asking for authentication pops up identity and password for 192.168.1.11 - I assume this is my Ubuntu password, fill it in and a second box pops up asking me for username and password for "Mesh", which is the WIN2000 box I am trying to print through. I fill in user name and password for admin on the Mesh as this is the user that has a password.

Host, gives me a list of boxes to choose from, so I choose Mesh (I don't know the IP address its set up for DHCP). There is no list of choices for Printer ( but in fact there are two printers connected to the Mesh) so I type in Samsung, which is the share name for the Samsung.

The user name and password in this dialog have now been automatically comlpeted with the Mesh user name and password from the Pop up box asking for them.

I choose forward and select Samsung CLP-500 from the printer list (I have already installed the drivers) 

The Driver dialog says Standard(CUPS) , and I choose apply.

The Samsng appears as a Printer, and I select properties and print test page.

I get an information box saying that a rest print is going to Samsung CLP-500, but nothing happens.

When I go to the Connection tab, the username is blank, but the password had  ******* in it as you would expect.

I give up waiting on something happening and click OK on the information box. 

The status of the printer stays at ready - No logon failure message.

Graham

---

### Post by myotis on 2006-03-01
To follow this up, I have now found my ip address for the Windows box with the printer attched and tried again, but still no joy.

Graham

---

### Post by Dylan103 on 2006-03-01
[http://ubuntuforums.org/showpost.php?p=783452&postcount=9](http://ubuntuforums.org/showpost.php?p=783452&postcount=9)
Go there and follow my sulution. Worked for me, probably will work for you.

---

### Post by myotis on 2006-03-01
Thanks, but I have already done all that, and it hasn't helped :-(

I am obviously missing some key step somewhere else.
Graham

---

### Post by Dylan103 on 2006-03-01
Did you do exactly what it says there? And type it all in correctly? Cause its 99% working.

---

### Post by myotis on 2006-03-01
[QUOTE=Dylan103]Did you do exactly what it says there? And type it all in correctly? Cause its 99% working.[/QUOTE]

As far as I can, in that the instructions don't include anything about usernames and passwords, and the printer is already set up as a share called Samsung, and I had already collected my IP address for the WIN2000 box.

What I am puzzled about is that I am asked for a password twice, once for 192.168.1.10, which is my WIN2000 box, and once for "Mesh" which is the name of the same WIn2000 box.

I am not asked for the Tusker username or password (the name of the box Ubuntu is installed on) yet the first help I got suggested that the Ubuntu username/password should be filled in, but these fields are autimaticallyy fiiled in with the Mesh username and password.

But of course I have tried every combination of username and password I can think of. Nothing makes any difference.

Graham

---

### Post by myotis on 2006-03-02
Ok, this is not as easy as it would seem. My laptop/docking station which prints through the same Windows box, as I am trying to print through with Ubuntu, has also decided to stop working. 

As the laptop is my main PC, which I use very day, and I know it was working fine before I started fiddling with Ubuntu, I have obviusly now broken something in the Windows networking side of things. :-(

So I shall now try and fix this, before coming back to this Ubuntu problem.

Thanks for everyones help so far.

Graham

---

### Post by dantheman on 2006-03-02
If it makes you feel any better, I'm having the same problem at work/school. I work in an office on campus and the IT department doesn't support linux... so I'm on my own. 

I know the IP of the printer.
I know the name of the printer.
I have a username and password (that's different than my Ubuntu login)

I get username/password verifications for 3 different IP addresses, but I should. Once it's installed correctly and all that jazz... I get an error:
```
NT_STATUS_UNSUCCESSFUL
```

Is this the windows box rejecting my user/pass? or is it something else? (as in myotis's case, I followed all the steps correctly to install the printer - even found a .ppd for my printer and am using that)

Any help would be fantastic, since I'm getting the hand from the IT department.
-Dan-

---

### Post by dantheman on 2006-03-02
to be completely accurate:
```
Ready: Connection failed with error NT_STATUS_UNSUCCESSFUL
```

---

### Post by myotis on 2006-03-03
[QUOTE=dantheman]If it makes you feel any better, -Dan-[/QUOTE]

Not really :-(

It seems from my searches that a few people have problems with this. 

Now that I have got my mini-network  working again, I have changed the usernames and passwords on my three boxes to be exctly the same,  and am going to try again.

Graham

---

### Post by darf681 on 2006-03-03
Don't know if this will help, and I can't tell if anybody else said this already (as it is 5:30am, and I have been working all nite and can't read)

1)  Make sure all boxes concerned have static IPs
2)  If you had to change them over to static, delete and reinstall the printer driver on your Ubuntu box
3)  Make sure when you install the driver on your Ubuntu box again, you input a user name and password during the install that is an account on the windows box.

hope this helps...

](*,)

---

### Post by myotis on 2006-03-03
Thanks everyone, but it seems I am looking in the wrong place for the problem.

As well as the Samsung, I have an HP Deskjet plugged into the WIN2000 box. I have now installed the Deskjet in exactlt the same way as I installed the Samsung, and the Deskjet works fine.

So the problem seems to be specifically with the Samsung, rather than the Ubuntu printing system.

Graham

---

