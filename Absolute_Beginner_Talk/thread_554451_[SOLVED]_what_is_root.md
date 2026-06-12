---
title: "[SOLVED] what is root?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by offline on 2007-09-19
Sorry for asking this simple one: what is root, root priviliges?

I mean I am the administrator(the boss) I suppose, and give priviliges to any other user. So in which instances the system blocks me from doing something and says "aah you are not rooot!"?

---

### Post by PmDematagoda on 2007-09-19
When you are about to do important changes to the system. This is a security measure used to prevent viruses(Never heard of Linux viruses though) or to prevent you from messing your own system up. :)

P.S: Root and root priviledges is like being the overlord of your Linux system. So be especially careful when running as root.

---

### Post by mivo on 2007-09-19
Here are two useful links, I believe: [definition at Wikipedia]("http://en.wikipedia.org/wiki/Root_user") and a bit more in-depth with a coverage of root privileges at [Linfo.org]("http://www.linfo.org/root.html").

---

### Post by exile on 2007-09-19
root is an equivalent (the original) unix version of the windows Administrator account.

---

### Post by aysiu on 2007-09-19
In Ubuntu and Mac OS X, *root* is more of an idea than an actual flesh-and-blood user.

*root* basically means the system.

When you are the "administrator" in Ubuntu or Mac OS X, you are most of the time a regular user. When you perform an administrative task (install software, change system-wide network or printer settings), you're prompted for password authentication in order to temporarily assume root-like privileges. Once you're done, you're back to a regular user.

More info here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by PmDematagoda on 2007-09-19
> **aysiu said:**
> In Ubuntu and Mac OS X, *root* is more of an idea than an actual flesh-and-blood user.

*root* basically means the system.

When you are the "administrator" in Ubuntu or Mac OS X, you are most of the time a regular user. When you perform an administrative task (install software, change system-wide network or printer settings), you're prompted for password authentication in order to temporarily assume root-like privileges. Once you're done, you're back to a regular user.

More info here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

This is why Windows is so vulnerable since you are the administrator at all times you are logged in(To your administrator account of course), this allows viruses to perform processes without wndows safe guards interfering since they are under the impression that it has been authorised by the user, this leads to a lot of damage by a virus unless ofcourse there is a virus guard.

---

### Post by Overbyte on 2007-09-19
> **exile said:**
> root is an equivalent (the original) unix version of the windows Administrator account.

Seconded. It is also called the **superuser (su)**
Root is the account that can do a lot of things, almost anything.

[quote=PmDematagoda]...or to prevent you from messing your own system up[/quote]

Hence root is like being God. :)
Root can play around with other user accounts.

[quote=offline]So in which instances the system blocks me from doing something and says "aah you are not rooot!"?[/quote]

Getting packages and messing with some hardware settings.

---

### Post by offline on 2007-09-19
OK, so since I HAVE been messing around and inadvertently changed the system settings( removed english language support trying to install another language from system>language support, how can I bring it back and install other languages support as well. Root privileges and terminal would do the work and how?(no internet connection)

ps login screen has only the default language as choice and system>language support is blank

---

### Post by lewac on 2007-09-21
uhh... well I found out WHEN *root* is not really **root**. for example coming from the "windows" world (like a lot of us beginning here with ubuntu) we're kinda used to accessing our ENTIRE system. once signed in (IF most of us at "home" even do that) we got the whole ball to play with. not the case here at all. because here we got ALL kinds of "permissions" to deal with. the perplexing one for me was "owners" of files, directories, and even entire partitions. thus when I attempted to create a new folder on an alternate ext2 partition it was a no-go EVEN though I sudo'd as root!

yeah I was running as "root" but I (administrator) was not the "owner" of that partition... root was. the boildown here is that we oughta be able to run as REAL root if we want to. sure we may muck things up but tell you what there ain't gonna be a lotta window users here that do NOT basically know what they are doing. so MY solution was to get LOGGED IN as root... not to just "run as root".

and somebody else found this way but its worth a repeat so here it is...

Here's how to do it in ubuntu:  Navigate to System/Administration/Login Window. You're presented with the Login Window Preferences window. On the Security tab there's an empty checkbox labeled “Allow local system administrator login”.  Check this box..  Now do the following (to set the password for  root): Go to System/Administration/Users and Groups. Enter YOUR User password. Select ''root'' in the Users settings window and press ''Properties”. Set and confirm a NEW password for  root in the Account 'root' Properties window. Click “ok/close”. Finally... reboot into ubuntu and login as root using this NEW password. You will be presented with a new desktop (which you may elect to configure as you wish). The main thing here is you have UNRESTRICTED ACCESS to your ENTIRE system! Log out as soon as you are complete with whatever you may be doing as  root though (btw you can “switch users” to do this or reboot).

and NOW to learn something about this linux! one of the reasons for that is we're not migrating our little network here to XP or Vista. those are even worse than the best OS Microsoft ever made (in our opinion win2000). now they're setting up shop to halt security support on winy2k ending 2010. yeah that's still a ways off but we all know about time slipping quickly by us too:(.

---

### Post by offline on 2007-10-13
> **lewac said:**
> uhh... well I found out WHEN *root* is not really **root**. for example coming from the "windows" world (like a lot of us beginning here with ubuntu) we're kinda used to accessing our ENTIRE system. once signed in (IF most of us at "home" even do that) we got the whole ball to play with. not the case here at all. because here we got ALL kinds of "permissions" to deal with. the perplexing one for me was "owners" of files, directories, and even entire partitions. thus when I attempted to create a new folder on an alternate ext2 partition it was a no-go EVEN though I sudo'd as root!

yeah I was running as "root" but I (administrator) was not the "owner" of that partition... root was. the boildown here is that we oughta be able to run as REAL root if we want to. sure we may muck things up but tell you what there ain't gonna be a lotta window users here that do NOT basically know what they are doing. so MY solution was to get LOGGED IN as root... not to just "run as root".

and somebody else found this way but its worth a repeat so here it is...

Here's how to do it in ubuntu:  Navigate to System/Administration/Login Window. You're presented with the Login Window Preferences window. On the Security tab there's an empty checkbox labeled “Allow local system administrator login”.  Check this box..  Now do the following (to set the password for  root): Go to System/Administration/Users and Groups. Enter YOUR User password. Select ''root'' in the Users settings window and press ''Properties”. Set and confirm a NEW password for  root in the Account 'root' Properties window. Click “ok/close”. Finally... reboot into ubuntu and login as root using this NEW password. You will be presented with a new desktop (which you may elect to configure as you wish). The main thing here is you have UNRESTRICTED ACCESS to your ENTIRE system! Log out as soon as you are complete with whatever you may be doing as  root though (btw you can “switch users” to do this or reboot).

and NOW to learn something about this linux! one of the reasons for that is we're not migrating our little network here to XP or Vista. those are even worse than the best OS Microsoft ever made (in our opinion win2000). now they're setting up shop to halt security support on winy2k ending 2010. yeah that's still a ways off but we all know about time slipping quickly by us too:(.

Thanks lewac, many times I  thought I can do any job in ubuntu just typing sudo before the command but nothing happened.

But, for example, if you are sudo-compiling and trying to install a package with ./configure, make, etc and the terminal returns error messages, are they meaningful
messages or just trash like many windows warnings.

 I mean if you are logged in as root may be you can install the above program with no questions asked but the result would be a not working program and trash spread all over???

---

### Post by Tomosaur on 2007-10-13
> **offline said:**
> Thanks lewac, many times I  thought I can do any job in ubuntu just typing sudo before the command but nothing happened.

But, for example, if you are sudo-compiling and trying to install a package with ./configure, make, etc and the terminal returns error messages, are they meaningful
messages or just trash like many windows warnings.

 I mean if you are logged in as root may be you can install the above program with no questions asked but the result would be a not working program and trash spread all over???

Generally, you should './configure && make' (one command by the way, saves a bit of time :P ) as a normal user. If you want to install the compiled program system wide, then you use 'sudo make install' as the final command. If you only want the program for yourself, then you just use 'make install'.

Generally, people want software system wide, so this is how you compile and install:
```

./configure && make && sudo make install

```

The '&&' just means 'do the next command after finishing the previous command' - it'll let you leave the terminal alone for a while.

Anyway, yes, generally speaking - in Linux you should read error messages. The problem with the terminal is that many people can't tell the difference between just verbose information, and actual error messages. For example, in the above 'compile and install' situation, the terminal will spit a LOT of information at you. You will even see a lot of stuff which LOOKS like errors, but aren't actually (mostly during the 'make' command - it's information for programmers really, a lot of it says stuff like 'undefined' or 'not found', but they're not errors, just information). For this reason, errors will usually come right at the end of the output, and if the error is serious enough, execution of the command will stop. For example:

When using the './configure' command, you'll get a lot of information, saying things like 'checking for library......no'. You can normally just ignore most of this - if there are serious problems then you will get something like the following right at the end of the output:
'ERROR: Couldn't find OpenGL libraries, please install and try again'. The whole point of the configure script is that it looks at what is available on your system, and sets the software to be compiled to use whatever's there. If something absolutely vital isn't there, then you'll get an error message.

The 'make' command spits out all kinds of crap - but generally speaking if the './configure' script executed with no problems, then the 'make' command shouldn't return any errors either. It's rare to find software which goes through the configure process fine then fails during compilation.

'make install' is generally just moving files about, there's almost no chance of error messages here.

So yeah, if you don't see OBVIOUS errors (ie, it should say 'ERROR' somewhere to count as an error), then you can just ignore pretty much everything it outputs to the terminal.

---

### Post by steve.horsley on 2007-10-13
I really think you should NOT be logging in as root. It's just asking for trouble. Instead, try this:

Try to separate in your mind the two different roles of system user and system administrator. If you are the owner of the computer, you will be both using and administrating it, but they really are two separate tasks. Most of the time you just want to use the system. On those occasions that you do administration like installing software, taking backups (of course you do) etc, be aware that this is not user activity, its sysadmin activity. Now, when running as a normal user, its just a question of putting on your sysadmin hat for a while every now and again. 

I run as a normal user, and when I have admin tasks to perform, I do one of two things. Some admin tasks can be done with a file manager, so I press Alt-F2 and enter the command **gksudo nautilus**. This gives me a file manager with full rights over the whole system. I have changed the background colour on mine so I can't forget its a root nautilus. And I close it as soon as I am done with the admin work. 

Some admin tasks are command-line tasks. For these, I open a terminal and enter the command **sudo -i**. This goves me a full root prompt (I don't like having to type sudo in front of every command, apart from which, some commands like piping don't work wlll with sudo). I do all my admin work in this root prompt, and then exit when the admin job is done. 

Neither typing gksudo  nautilus or typing sudo -i is overly difficult, and this is much, much safer than logging in as root. 

Oh, and if you ger permission denied when working as root, there is something else wrong, like you are trying to write to a read-only filesystem, for instance trying to delete a file on a CD-ROM.

---

