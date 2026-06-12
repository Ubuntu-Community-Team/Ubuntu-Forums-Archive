---
title: "AIM Install?"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by That Guy X on 2006-11-27
Can someone please give me instructions on how to install AIM, I like GAIM but all my friends use AIM and when I talk to them my font either mimicks thiers, or its a totaly different color[-(

---

### Post by HokeyFry on 2006-11-27
try the AIM website, although ive never successfully been able to install it. i dont remember what went wrong though so i cant help u there.

However i also am interested in this so if anyone has successfully installed AIM on Ubuntu your help would be greatly appreciated.

---

### Post by Foudre on 2006-11-27
i know it can be done, i remember i had it installed  awhile back, on a previous install of ubunutu, don't realy remeber though

---

### Post by That Guy X on 2006-11-27
I did the instructions on the AIM website and I got this ](*,) 

sudo dpkg -i aim_1.5.286-2.i386.deb
Password:
dpkg: error processing aim_1.5.286-2.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 aim_1.5.286-2.i386.deb

---

### Post by Niclo on 2007-08-05
OK I'm extremely new to any distro of linux.  In fact this is the first one I've been ever to use enough to install items. So here's the lowdown on how to get your AIM to install.

FIRST:  go to [www.microsoft.com](www.microsoft.com) go to downloads or search for IE 6 (Internet Explorer 6).  Once you get to their download page download  IE6 Installer for win2k/xp. Or click this link and download it [http://www.microsoft.com/downloads/details.aspx?FamilyID=1e1550cb-5e5d-48f5-b02b-20b602228de6&DisplayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=1e1550cb-5e5d-48f5-b02b-20b602228de6&DisplayLang=en)

Now that you have your installer downloaded run WINE and run the installer.  Just follow the steps and let it run its course. 

Once IE6 is installed use WINE to run your install of AIM and it will follow through totally fine.  Then run AIM and enjoy.

---

### Post by bubba2120 on 2007-08-06
i dont think he wants to emulate it just how to install the linux version

alright heres what you do

1. Log in as root
2. Download the aim_1.5.286-2_i386.deb file from [Here]("http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb")
3. Save it to a folder called aim on your desktop
4. Open terminal and type "cd /home/root/Desktop/aim"
5. Type in command "dpkg -i aim_1.5.286-2_i386.deb"
6. To run type "/usr/local/bin/aim" in the terminal

---

### Post by Zedd on 2007-08-06
> **bubba2120 said:**
> i dont think he wants to emulate it just how to install the linux version

alright heres what you do

1.** Log in as root**
2. Download the aim_1.5.286-2_i386.deb file from [Here]("http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb")
3. Save it to a folder called aim on your desktop
4. Open terminal and type "cd /home/root/Desktop/aim"
5. Type in command "dpkg -i aim_1.5.286-2_i386.deb"
6. To run type "/usr/local/bin/aim" in the terminal


Please don't. Logging in as root is dangerous and is never suggested. Besides, then you'd have to create a password for your root account. While this is not hard, it's not very safe. I'd just do this from a terminal

```
wget http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb
sudo dpkg -i aim_1.5.286-2_i386.deb
```

Then, it should create an entry in the menu, under internet. If it doesn't you can either run "aim" from a terminal, or you can create a launcher for it, by having it run the command "aim"

That should be all you need! Good luck!

---

### Post by dasunst3r on 2007-08-06
GAIM (now known as Pidgin) allows you to connect to the AIM network in addition to many other networks.  There is honestly no need to install AIM.  As a matter of fact, I would even venture to say that the official Linux client for AIM looks like a scar on the desktop!

---

### Post by bubba2120 on 2007-08-06
its only dangerous to log in as root if you go to malicious sites or if you dont know what your doing and its still unlikely anything could happen

---

### Post by irish_flu on 2007-08-06
> **bubba2120 said:**
> its only dangerous to log in as root if you go to malicious sites or if you dont know what your doing and its still unlikely anything could happen

Even if you do "know what you're doing", everybody makes mistakes.  It's better to have that extra layer of not being logged in with admin rights; you have to try that much harder to make a mistake.

---

### Post by bubba2120 on 2007-08-07
i guess but still i always log into root and havnt had one problem yet. but i guess theres always a chance

---

### Post by oneyozfest182 on 2007-09-13
```
ozzy@ozzy-laptop:~$ sudo dpkg -i aim_1.5.286-2_i386.deb
dpkg-deb: file looks like it might be an archive which has been
dpkg-deb:    corrupted by being downloaded in ASCII mode
dpkg-deb: `aim_1.5.286-2_i386.deb' is not a debian format archive
dpkg: error processing aim_1.5.286-2_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 aim_1.5.286-2_i386.deb
```
:(

---

### Post by sstusick on 2007-09-13
I recommend using GAIM/Pidgin... the AIM for Linux is outdated and works very poorly.

---

### Post by avik on 2007-09-13
> **bubba2120 said:**
> i guess but still i always log into root and havnt had one problem yet. but i guess theres always a chance

You might as well be using Windows for all the malware you can easily get.  Security isn't a product; it's a state of mind.

---

### Post by llamakc on 2007-09-13
> **bubba2120 said:**
> i guess but still i always log into root and havnt had one problem yet. but i guess theres always a chance

Stay off the computer drunk.

---

### Post by akba0012 on 2007-09-13
> **Zedd said:**
> Please don't. Logging in as root is dangerous and is never suggested. Besides, then you'd have to create a password for your root account. While this is not hard, it's not very safe. I'd just do this from a terminal

```
wget http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb
sudo dpkg -i aim_1.5.286-2_i386.deb
```

Then, it should create an entry in the menu, under internet. If it doesn't you can either run "aim" from a terminal, or you can create a launcher for it, by having it run the command "aim"

That should be all you need! Good luck!

Shoot, unfortunately, it gave me this
 
```
root@Central:/home/fahim/Desktop/aim# sudo dpkg -i aim_1.5.286-2_i386.deb
dpkg-deb: file looks like it might be an archive which has been
dpkg-deb:    corrupted by being downloaded in ASCII mode
dpkg-deb: `aim_1.5.286-2_i386.deb' is not a debian format archive
dpkg: error processing aim_1.5.286-2_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 aim_1.5.286-2_i386.deb

```


umm?

---

### Post by oneyozfest182 on 2007-09-13
I said the same thing but no one seemed to help me. :(

---

### Post by Maestro23 on 2007-09-13
> **oneyozfest182 said:**
> I said the same thing but no one seemed to help me. :(

Got a link to where you d/l the .deb?

---

### Post by sstusick on 2007-09-13
Why go through all this trouble for crappy AIM? Pidgin is fine, KoPete is another option...

---

### Post by nonewmsgs on 2007-09-13
the guy isn't satisified with gaim or a multi-messenger.  if he wants aim and he can have aim, let's try to get it to him like the good man who is asking the deb link or even the new fellow with the  wine instructions did.  he already mentioned in the inital post he needs it and there are times i need gyeiche or amsn so i can understand that.

---

### Post by llamakc on 2007-09-14
> **nonewmsgs said:**
> the guy isn't satisified with gaim or a multi-messenger.  if he wants aim and he can have aim, let's try to get it to him like the good man who is asking the deb link or even the new fellow with the  wine instructions did.  he already mentioned in the inital post he needs it and there are times i need gyeiche or amsn so i can understand that.

So what's your answer to help the OP?

OP: provide the link where you downloaded the package, please.

---

### Post by oneyozfest182 on 2007-09-14
^I love "nonewmessages'" attitude!

Oh, and his signature. :P

---

### Post by Maestro23 on 2007-09-14
> **oneyozfest182 said:**
> ^I love "nonewmessages'" attitude!

Oh, and his signature. :P

Do you have the link to where you d/l the .deb?  We're trying to help ya. :smile:

---

### Post by oneyozfest182 on 2007-09-14
> **Zedd said:**
> ```
wget http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb
sudo dpkg -i aim_1.5.286-2_i386.deb
```

Then, it should create an entry in the menu, under internet. If it doesn't you can either run "aim" from a terminal, or you can create a launcher for it, by having it run the command "aim"

That should be all you need! Good luck!
I used this.

---

### Post by nonewmsgs on 2007-09-14
> **oneyozfest182 said:**
> I used this.

[http://ftp.newaol.com/aimgen/380469/](http://ftp.newaol.com/aimgen/380469/)
and select the 234 one.  (aim-1.5.234-1.i386.deb)

the other ones gave the same error you gave in your initial post.  

```

wget http://ftp.newaol.com/aimgen/380469/aim-1.5.234-1.i386.deb
sudo dpkg -i aim-1.5.234-1.i386.deb

```

or you can just download it from the ftp site i gave and open with the GDepi package installer.:guitar:

---

### Post by typeadam on 2007-11-17
> **nonewmsgs said:**
> or you can just download it from the ftp site i gave and open with the GDepi package installer.:guitar:

This is my first post on this forum!
I dug this thread up while searching for AIM for Ubuntu. I'm a n00bie to this whole thing so I know nothing right now.

But my question is, I followed your instruction, downloaded the file, clicked it and it said it installed it but how do I launch it?? It is not in the menu and I have no idea how to proceed.

Please let me know.
Thanks

---

### Post by madmatrixz3000 on 2007-11-17
use "sudo --su" all root possibilities, much safer.

And yeah why use AIM just update pidgin, none of my friends can tell the dif even in vid chat!

---

### Post by llamakc on 2007-11-17
```

sudo -i

```

Is the preferred method for any extended amount of time to perform 'root' tasks.

---

### Post by typeadam on 2007-11-17
> **llamakc said:**
> ```

sudo -i

```

Is the preferred method for any extended amount of time to perform 'root' tasks.

It says cannot execute binary file. But I don't know if I ran the command well...

should it be:      sudo -i aim

Again, I have NEVER used this environment and I'm just starting out.

TO the other poster, I probably will use the other program, but I'm still curious about why this won't launch or how I should launch it.

Thank you

---

### Post by llamakc on 2007-11-17
Are you trying to run AIM, the Windows program on Linux? 

Don't. Use Pidgin as mentioned already.

---

### Post by typeadam on 2007-11-17
yes, AIM. Several posts up there was a link to AIM which I thought was supposed to be made for Linux. I downloaded it. It installed itself - gave me no errors. But there is nothing in the menu, nor am I able to launch it.

I'm aware of Pidgin. I've used it before, and I'll continue to use it. However, seeing that I'm not able to launch a program, I'm hoping I can learn from this so that if it ever happens in the future to ANOTHER program I'll know how to launch it properly using the terminal or however else.

In addition, there was another post several posts up about putting it in the menu using the terminal.

Again, I'm a complete beginner at this and I apologize if these are stupid questions but I'll learn I just need to be pointed in the right direction.

Thanks,

---

### Post by llamakc on 2007-11-17
No no, my bad for not reading the context. 

Open a terminal and type:

```

dpkg -L aim

```

It's going to return every file installed when you installed the aim*.deb. Post the output back here and I'll tell you which one it is.

---

### Post by maybeway36 on 2007-11-17
Can't you just install the windows fonts, and use those?

---

### Post by typeadam on 2007-11-17
```
/.
/usr
/usr/local
/usr/local/bin
/usr/local/bin/aim
/usr/local/lib
/usr/local/lib/aim
/usr/local/lib/aim/CoolBos.so.1
/usr/local/lib/aim/CoolBucky.so.1
/usr/local/lib/aim/CoolSocket.so.1
/usr/local/lib/aim/CoolSos.so.1
/usr/local/lib/aim/extra
/usr/local/lib/aim/extra/AIM.desktop
/usr/local/lib/aim/extra/AOL Instant Messenger (SM).desktop
/usr/local/lib/aim/extra/aim.png
/usr/local/lib/aim/extra/aim.xpm
/usr/local/lib/aim/extra/install.sh
/usr/local/lib/aim/feed.so.1
/usr/local/lib/aim/help
/usr/local/lib/aim/help/about_buddy_privacy.htm
/usr/local/lib/aim/help/about_the_buddy_list.htm
/usr/local/lib/aim/help/adding_a_group_or_buddy.htm
/usr/local/lib/aim/help/after_regis.htm
/usr/local/lib/aim/help/allowing_everyone_to_send_you_me.htm
/usr/local/lib/aim/help/allowing_only_your_buddies_to_se.htm
/usr/local/lib/aim/help/allowing_specific_users_to_conta.htm
/usr/local/lib/aim/help/away_message.htm
/usr/local/lib/aim/help/away_prefs.htm
/usr/local/lib/aim/help/banner.htm
/usr/local/lib/aim/help/banner_2.htm
/usr/local/lib/aim/help/blocking_everyone_from_sending_y.htm
/usr/local/lib/aim/help/blocking_specific_users.htm
/usr/local/lib/aim/help/changing_address.htm
/usr/local/lib/aim/help/changing_password.htm
/usr/local/lib/aim/help/chat.htm
/usr/local/lib/aim/help/chat_invite.htm
/usr/local/lib/aim/help/confirming_account.htm
/usr/local/lib/aim/help/connection_prefs.htm
/usr/local/lib/aim/help/defining_away.htm
/usr/local/lib/aim/help/deleting_a_group.htm
/usr/local/lib/aim/help/deleting_away.htm
/usr/local/lib/aim/help/format_messages.htm
/usr/local/lib/aim/help/fs_about_bl.htm
/usr/local/lib/aim/help/fs_about_buddy_privacy.htm
/usr/local/lib/aim/help/fs_about_the_buddy_list.htm
/usr/local/lib/aim/help/fs_adding_a_group_or_buddy.htm
/usr/local/lib/aim/help/fs_after_regis.htm
/usr/local/lib/aim/help/fs_allowing_only_your_buddies.htm
/usr/local/lib/aim/help/fs_allowing_specific_users_to_con.htm
/usr/local/lib/aim/help/fs_away_message.htm
/usr/local/lib/aim/help/fs_chat.htm
/usr/local/lib/aim/help/fs_away_prefs.htm
/usr/local/lib/aim/help/fs_blocking_specific_users.htm
/usr/local/lib/aim/help/fs_changing_address.htm
/usr/local/lib/aim/help/fs_changing_password.htm
/usr/local/lib/aim/help/fs_chat_invite.htm
/usr/local/lib/aim/help/fs_confirming_account.htm
/usr/local/lib/aim/help/fs_connection_prefs.htm
/usr/local/lib/aim/help/fs_deleting_a_group.htm
/usr/local/lib/aim/help/fs_everyone_from_sending.htm
/usr/local/lib/aim/help/fs_format_messages.htm
/usr/local/lib/aim/help/fs_general_prefs.htm
/usr/local/lib/aim/help/fs_im.htm
/usr/local/lib/aim/help/fs_insert_hyperlink.htm
/usr/local/lib/aim/help/fs_insert_smileys.htm
/usr/local/lib/aim/help/fs_installing.htm
/usr/local/lib/aim/help/fs_privacy_prefs.htm
/usr/local/lib/aim/help/fs_registering.htm
/usr/local/lib/aim/help/fs_sending_chat.htm
/usr/local/lib/aim/help/fs_sending_im.htm
/usr/local/lib/aim/help/fs_signing_on.htm
/usr/local/lib/aim/help/fs_sounds.htm
/usr/local/lib/aim/help/fs_sounds_prefs.htm
/usr/local/lib/aim/help/fs_turning_an_away.htm
/usr/local/lib/aim/help/fs_uninstalling.htm
/usr/local/lib/aim/help/general_prefs.htm
/usr/local/lib/aim/help/help_contents.htm
/usr/local/lib/aim/help/im.htm
/usr/local/lib/aim/help/im_hyperlink.htm
/usr/local/lib/aim/help/images
/usr/local/lib/aim/help/images/BL.gif
/usr/local/lib/aim/help/images/add_buddy.gif
/usr/local/lib/aim/help/images/aimheaderleft.gif
/usr/local/lib/aim/help/images/away.gif
/usr/local/lib/aim/help/images/buddyList.gif
/usr/local/lib/aim/help/images/chat_invite_scr.gif
/usr/local/lib/aim/help/images/chat_message.gif
/usr/local/lib/aim/help/images/chat_message2.gif
/usr/local/lib/aim/help/images/im.gif
/usr/local/lib/aim/help/images/sign_on.gif
/usr/local/lib/aim/help/index.htm
/usr/local/lib/aim/help/insert_hyperlink.htm
/usr/local/lib/aim/help/insert_smileys.htm
/usr/local/lib/aim/help/installing.htm
/usr/local/lib/aim/help/inviting.htm
/usr/local/lib/aim/help/overview.htm
/usr/local/lib/aim/help/privacy_prefs.htm
/usr/local/lib/aim/help/registering.htm
/usr/local/lib/aim/help/saving_im.htm
/usr/local/lib/aim/help/sending_chat.htm
/usr/local/lib/aim/help/sending_im.htm
/usr/local/lib/aim/help/signing_on.htm
/usr/local/lib/aim/help/sounds_prefs.htm
/usr/local/lib/aim/help/turning_an_away.htm
/usr/local/lib/aim/help/uninstalling.htm
/usr/local/lib/aim/service.so.1
/usr/local/lib/aim/sounds
/usr/local/lib/aim/sounds/dooropen.wav
/usr/local/lib/aim/sounds/doorslam.wav
/usr/local/lib/aim/sounds/imrcv.wav
/usr/local/lib/aim/sounds/imsend.wav
/usr/local/lib/aim/sounds/ring.wav
/usr/local/lib/aim/source
/usr/local/lib/aim/source/extgtktext.c
/usr/local/lib/aim/source/extgtktext.h
/usr/local/lib/aim/source/line-arrow.xbm
/usr/local/lib/aim/source/line-wrap.xbm
/usr/local/lib/aim/ui.so.1
/usr/local/lib/libXpcs.so.1
/usr/local/lib/libXprt.so.1
/usr/local/lib/libXptl.so.1
/usr/local/lib/libextgtk.so.1
/usr/doc
/usr/doc/aim
/usr/doc/aim/copyright
/usr/doc/aim/changelog.Debian.gz
/usr/local/lib/aim/CoolBos.so
/usr/local/lib/aim/CoolBucky.so
/usr/local/lib/aim/CoolSocket.so
/usr/local/lib/aim/CoolSos.so
/usr/local/lib/aim/feed.so
/usr/local/lib/aim/service.so
/usr/local/lib/aim/ui.so
/usr/local/lib/libXpcs.so
/usr/local/lib/libXprt.so
/usr/local/lib/libXptl.so
/usr/local/lib/libextgtk.so
```

---

### Post by llamakc on 2007-11-17
You need to create a launcher or menu item that points to /usr/local/bin/aim or run it from the commandline (or ALT-F2) with the full path.

```

/usr/local/bin/aim

```

---

### Post by madmatrixz3000 on 2007-11-17
SERIOULY if you use the updated pidgin, it is the same as AIM!  No formating issues or anything!

---

### Post by typeadam on 2007-11-17
Made a launcer on the desktop as a test and nothing happens. I don't even hear my hard drive grinding...
Maybe the file is just busted...
If I want to remove it, I can remove the installation can I do that via "synaptic package manager" or is there another way to completely remove/uninstall a program.

---

### Post by llamakc on 2007-11-17
dpkg -r aim

---

### Post by Urbandale on 2007-11-17
OK guys, jesus. He ALREADY SAID he doesn't want GAIM! 

Stop giving him what he DOESN'T WANT! Its this kind of eliteism that makes Debian/Ubuntu look bad!

---

### Post by llamakc on 2007-11-17
> **Urbandale said:**
> OK guys, jesus. He ALREADY SAID he doesn't want GAIM! 

Stop giving him what he DOESN'T WANT! Its this kind of eliteism that makes Debian/Ubuntu look bad!

Are you reading the thread? I showed him WHERE the package installed to, instructed him on how to launch it. Now HE wants to remove it.

Relax, preach.

---

### Post by Urbandale on 2007-11-17
yeah, he wants to delete it, but, unless I'm mistaken, he's probably going to reinstall, as it seems his install was bed

---

### Post by typeadam on 2007-11-17
it says "requested operation requires superuser privilege"

---

### Post by Urbandale on 2007-11-17
sudo dpkg -r aim

---

### Post by typeadam on 2007-11-17
Thank you.
I'll just stick w/ Pidgin...

---

### Post by mdinfamy on 2007-11-20
Hm what is root?  Is root the first username I made on the computer.  For example if I go to try to set up the network as manual configuration it asks me for a password first, then I enter it in and it works.  Does that mean I'm always using root?

---

### Post by sstusick on 2007-11-20
Root = Administrator

---

### Post by Ronaldbain99 on 2007-11-20
I end up getting this message every time I run AIM

aim: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

I don't know what to do here...

---

### Post by itsvan on 2008-03-17
I HAVE PIGEON and it runs awesome,,but i cant seem to SEND FILES to my friend,,he has WINDOWS XP using AIM,,waht can i do to fix that???

---

### Post by jrusso2 on 2008-03-17
> **Ronaldbain99 said:**
> I end up getting this message every time I run AIM

aim: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

I don't know what to do here...

Yes there does not seem to be a way to get this to work.  On another computer I have Netscape installed for linux and it has AIM integrated into it.

Its the version of netscape that has the email client and web client integrated.

---

### Post by lild5491 on 2008-06-21
> **Zedd said:**
> Please don't. Logging in as root is dangerous and is never suggested. Besides, then you'd have to create a password for your root account. While this is not hard, it's not very safe. I'd just do this from a terminal

```
wget http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb
sudo dpkg -i aim_1.5.286-2_i386.deb
```

Then, it should create an entry in the menu, under internet. If it doesn't you can either run "aim" from a terminal, or you can create a launcher for it, by having it run the command "aim"

That should be all you need! Good luck!

I followed your directions, but still have failed to install aim, i got the following message: "dpkg-deb: file looks like it might be an archive which has been
dpkg-deb:    corrupted by being downloaded in ASCII mode
dpkg-deb: `aim_1.5.286-2_i386.deb' is not a debian format archive
dpkg: error processing aim_1.5.286-2_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:"

---

### Post by slayr007 on 2008-06-26
this code didn't work for me

Please don't. Logging in as root is dangerous and is never suggested. Besides, then you'd have to create a password for your root account. While this is not hard, it's not very safe. I'd just do this from a terminal

"Code:

wget [http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb](http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb)
sudo dpkg -i aim_1.5.286-2_i386.deb

Then, it should create an entry in the menu, under internet. If it doesn't you can either run "aim" from a terminal, or you can create a launcher for it, by having it run the command "aim"

That should be all you need! Good luck!"

I get an error 404 message

Why is this?

---

