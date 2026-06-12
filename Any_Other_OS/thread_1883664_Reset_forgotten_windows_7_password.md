---
title: "Reset forgotten windows 7 password"
date: 2011-11-19
forum: Any Other OS
---

### Post by jodiaq on 2011-11-19
hi,
i have tried to reset the windows 7 password using ubuntu 11.10. i tried the following commands.
[FONT=Arial][SIZE=2][COLOR=red]cd /media/XXXXXXXXXX/Windows/System32/config/[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=red]chntpw -l SAM[/COLOR][/SIZE][/FONT]
It said no such file of directory
ls
[FONT=Arial][SIZE=2][COLOR=red]chntpw -l sam[/COLOR][/SIZE][/FONT]
it showed the list of users
i took the admin one and gave the command as
[FONT=Arial][SIZE=2][COLOR=red]chntpw -u Administrator sam[/COLOR][/SIZE][/FONT]
then entered new password
save yes.
ok
all went allright in ubuntu, then gave reboot
the system rebooted and the login screen of win7 came up asking for the password.
Then entered the new password i gave. But failed to login. 
i tried this for few times but there are no results. 
Can any one tell me a way to reset password of win 7 using ubuntu.

---

### Post by lisati on 2011-11-19
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by Gremlinzzz on 2011-11-20
[http://pcsupport.about.com/od/toolsofthetrade/gr/ophcrack.htm](http://pcsupport.about.com/od/toolsofthetrade/gr/ophcrack.htm)

:popcorn:never had to use it but its free and i read its the best one:popcorn:



[http://pcsupport.about.com/od/toolsofthetrade/tp/passrecovery.htm](http://pcsupport.about.com/od/toolsofthetrade/tp/passrecovery.htm)


others on list

---

### Post by jodiaq on 2011-11-20
i tried that ophcrack it shows the list of users as shown
[IMG]http://i42.tinypic.com/33tpggh.png[/IMG]
what to do next.

---

### Post by Megaptera on 2011-11-20
I used this guide [http://www.psychocats.net/ubuntucat/resetwindowspassword/](http://www.psychocats.net/ubuntucat/resetwindowspassword/)
and left the p/w blank 'til I rebooted in to Windows 7 & _then_ re-set p/w when in Windows.
That worked for me, hope it helps?

---

### Post by SoFl W on 2011-11-20
Once you solve that problem I would suggest:
[http://www.keepassx.org/](http://www.keepassx.org/)

---

### Post by jodiaq on 2011-11-20
this is what i have done.
```
                                  jodiaq@jodiaq-nl:/media/529C5AB99C5A9777/Windows/System32/config$ chntpw -l sam
 

 chntpw version 0.99.6 080526 (sixtyfour), (c) Petter N Hagen
 

 Hive <sam> name (from header): <\SystemRoot\System32\Config\SAM>
 

 ROOT KEY at offset: 0x001020 * Subkey indexing type is: 666c <lf>
 

 Page at 0x10000 is not 'hbin', assuming file contains garbage at end
 

 File size 262144 [40000] bytes, containing 7 pages (+ 1 headerpage)
 

 Used for data: 247/52224 blocks/bytes, unused: 10/8992 blocks/bytes.
 

 

 

 

 

 * SAM policy limits:
 

 Failed logins before lockout is: 0
 

 Minimum password length        : 0
 

 Password history count         : 0
 

 | RID -|---------- Username ------------| Admin? |- Lock? --|
 

 | 01f4 | Administrator                  | ADMIN  |          |
 

 | 01f5 | Guest                          |        | dis/lock |
 

 | 03e8 | ss                             | ADMIN  |          |
 

 jodiaq@jodiaq-nl:/media/529C5AB99C5A9777/Windows/System32/config$ chntpw -u ss sam
 

 chntpw version 0.99.6 080526 (sixtyfour), (c) Petter N Hagen
 

 Hive <sam> name (from header): <\SystemRoot\System32\Config\SAM>
 

 ROOT KEY at offset: 0x001020 * Subkey indexing type is: 666c <lf>
 

 Page at 0x10000 is not 'hbin', assuming file contains garbage at end
 

 File size 262144 [40000] bytes, containing 7 pages (+ 1 headerpage)
 

 Used for data: 247/52224 blocks/bytes, unused: 10/8992 blocks/bytes.
 

 

 

 

 

 * SAM policy limits:
 

 Failed logins before lockout is: 0
 

 Minimum password length        : 0
 

 Password history count         : 0
 

 | RID -|---------- Username ------------| Admin? |- Lock? --|
 

 | 01f4 | Administrator                  | ADMIN  |          |
 

 | 01f5 | Guest                          |        | dis/lock |
 

 | 03e8 | ss                             | ADMIN  |          |
 

 

 

 ---------------------> SYSKEY CHECK <-----------------------
 

 SYSTEM   SecureBoot            : -1 -> Not Set (not installed, good!)
 

 SAM      Account\F             : 0 -> off
 

 SECURITY PolSecretEncryptionKey: -1 -> Not Set (OK if this is NT4)
 

 Syskey not installed!
 

 

 

 RID     : 1000 [03e8]
 

 Username: ss
 

 fullname: akhilesh
 

 comment :  
 

 homedir :  
 

 

 

 User is member of 1 groups:
 

 00000220 = Administrators (which has 2 members)
 

 

 

 Account bits: 0x0214 =
 

 [ ] Disabled        | [ ] Homedir req.    | [X] Passwd not req. |  
 

 [ ] Temp. duplicate | [X] Normal account  | [ ] NMS account     |  
 

 [ ] Domain trust ac | [ ] Wks trust act.  | [ ] Srv trust act   |  
 

 [X] Pwd don't expir | [ ] Auto lockout    | [ ] (unknown 0x08)  |  
 

 [ ] (unknown 0x10)  | [ ] (unknown 0x20)  | [ ] (unknown 0x40)  |  
 

 

 

 Failed login count: 0, while max tries is: 0
 

 Total  login count: 47
 

 

 

 - - - - User Edit Menu:
 

  1 - Clear (blank) user password
 

  2 - Edit (set new) user password (careful with this on XP or Vista)
 

  3 - Promote user (make user an administrator)
 

 (4 - Unlock and enable user account) [seems unlocked already]
 

  q - Quit editing user, back to user select
 

 Select: [q] > 1
 

 

 

 Hives that have changed:
 

  #  Name
 

  0  <sam>
 

 Write hive files? (y/n) [n] : y
 

  0  <sam> - OK
 

 jodiaq@jodiaq-nl:/media/529C5AB99C5A9777/Windows/System32/config$ 
 

 
```but it's a failure.
i haven't seen the [http://www.keepassx.org/](http://www.keepassx.org/) after checking that
i'll come back with the result.
by the way thanks for the quick responses.

---

### Post by Mandom on 2011-11-22
Try to follow this vide guide if you want to reset forgotten windows 7 password

 [http://www.youtube.com/watch?v=ftWsCrc0p1M ]("http://www.youtube.com/watch?v=ftWsCrc0p1M")

---

### Post by Rumor on 2011-11-23
I've used System Rescue CD [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)) in the past to successfully reset forgotten Windows 7 passwords.

System Rescue CD is a Gentoo based live CD. It boots to a CLI interface, but you can startx if you want a GUI interface.

Best of luck.

---

### Post by infiniteone on 2011-11-24
> **Megaptera said:**
> I used this guide [http://www.psychocats.net/ubuntucat/resetwindowspassword/](http://www.psychocats.net/ubuntucat/resetwindowspassword/)
and left the p/w blank 'til I rebooted in to Windows 7 & _then_ re-set p/w when in Windows.
That worked for me, hope it helps?

This guide works I used this and another using more of the command line but all in all it works the main change is at the end when asked and I quote the document

> [SIZE="2"]"this part is important"[/SIZE]

choose option #4 and>  "promote another user to administrator"  hopefully you have another user account which you can do this with if not you have another issue all together

after which you'll be asked do you want to execute > [SIZE="2"]"y=yes"[/SIZE]  then quit and reboot in to the windows account you just promoted / (hopefully you have the password for this account), you should have admin privileges/ meaning you should be able to reset the account with the lost password

the metod of clearing the password (method 1) didn't work for me using a usb drive from boot on Windows 7 Home Premium of course it had nothing to do with the drive but maybe something different with Windows 7 Home Premium

---

### Post by baldiehead on 2011-11-24
> **jodiaq said:**
> i tried that ophcrack it shows the list of users as shown
[IMG]http://i42.tinypic.com/33tpggh.png[/IMG]
what to do next.

One probable reason why it did not work is cause it can only crack dictionary and numerical passwords using the free rainbow tables. Anyway one possible (but not very fast) way is for you to take the NT hash and post it here and see if anyone willing to help you crack: [https://www.freerainbowtables.com/phpBB3/uncracked-hashes-f23.html](https://www.freerainbowtables.com/phpBB3/uncracked-hashes-f23.html). Remember to tell them what kinda hash it is, so if they help, they can run it thru their massive rainbow tables. Good luck.

---

### Post by Megaptera on 2011-11-24
> **infiniteone said:**
> This guide works I used this and another using more of the command line but all in all it works the main change is at the end when asked and I quote the document



choose option #4 and hopefully you have another user account which you can do this with if not you have another issue all together

after which you'll be asked do you want to execute   then quit and reboot in to the windows account you just promoted / (hopefully you have the password for this account), you should have admin privileges/ meaning you should be able to reset the account with the lost password

the metod of clearing the password (method 1) didn't work for me using a usb drive from boot on Windows 7 Home Premium of course it had nothing to do with the drive but maybe something different with Windows 7 Home Premium

I'm confused here, are you talking about a problem you're having - in which case please 'report' your post and ask for it to be moved to its own thread.
If you're trying to help the original poster (o/p) could you clraify your advice please?

Thanks.

---

