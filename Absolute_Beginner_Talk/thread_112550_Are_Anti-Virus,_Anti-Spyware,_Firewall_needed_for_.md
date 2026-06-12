---
title: "Are Anti-Virus, Anti-Spyware, Firewall needed for Ubunta?"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by The Pinny Parlour on 2006-01-04
Are Anti-Virus, Anti-Spyware, Firewall needed for Ubunta?
If so what are recommended.  If not, why not

Thank you

---

### Post by byen on 2006-01-04
Antivirus: Nope not necessary unless you want to scan your windows drive with it. Linux cant be easily infected and there are not many viruses that can infect a linux box.
AntiSpyware: Nope. (ah the joy of linux ;-) )
Firewall: Nope. But i do recommend having one anyways. The most simple and effective would be "firestarter"
code for terminal : sudo apt-get install firestarter

Hope this helps. goodluck.

---

### Post by shade11 on 2006-01-04
Yes the firewall is something you want.

But if you cant live without an antivirus. (Like me.)

Then get ClamAV

```
sudo apt-get install clamav
```

or download panda Antivirus
[http://www.pandasoftware.com/download/linux.htm]("http://www.pandasoftware.com/download/linux.htm")
If you dont know how to install look in the wiki or ask in the forum.

As for anti-spyware. No need.

---

### Post by The Pinny Parlour on 2006-01-04
You guys are great here.  Thank you   Awesome:D

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=byen]. The most simple and effective would be "firestarter"
code for terminal : sudo apt-get install firestarter

Hope this helps. goodluck.[/QUOTE]


Hello,

Have down as you suggest and get the following:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Perfect Storm on 2006-01-06
You've properly synaptic Package manager running at the same time, Make sure to close it first.

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=Artificial Intelligence]You've properly synaptic Package manager running at the same time, Make sure to close it first.[/QUOTE]

Thank you.

I have tried it again and get the following:

@ubuntu:~$ sudo apt-get install firestarter
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter
@ubuntu:~$

---

### Post by Perfect Storm on 2006-01-06
You have to enable universe: Here's how you do - [http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by earobinson on 2006-01-06
Originally Posted by earobinson
a simple search for security and you find lots on this

[http://www.ubuntuforums.org/showthre...light=security]("http://www.ubuntuforums.org/showthread.php?t=9836&highlight=security")
[http://www.ubuntuforums.org/showthre...light=security]("http://www.ubuntuforums.org/showthread.php?t=98912&highlight=security") <- good debate

---

### Post by manofsteel on 2006-01-06
You might want to try opening the other repositories if you have not done so or try automatix, [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
after it installs go to your aplications menue to find it, and run it. then check all the stuff you want installed, including firestarter with start-up on login ;)

---

### Post by The Pinny Parlour on 2006-01-06
This does not work:
2.3.	

How do I add Universe and Multiverse?
	

By default, Ubuntu comes pre-configured with basic and security update repositories. To enable the extra Universe and Multiverse repositories:

   1.

      Start Synaptic by selecting System->Administration->Synaptic Package Manager from the desktop menu system.
   2.

      In Synaptic choose Settings-> Repositories.
   3.

      Click the Settings button.
   4.

      Tick Show disabled software sources, then click Close.
   5.

      On the Repositories dialog box click Add. There are three separate repositories; Breezy Badger, Security Updates and Updates. Select each repository and check Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse). Ensure you click OK between each repository to save your changes.
   6.

      You should now see checkboxes next to each repository, scroll through the list and ensure they are all checked. 



There is no 'repositores' listed.
I had to search for it.
Nothing else said above is listed.

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=earobinson]Originally Posted by earobinson
a simple search for security and you find lots on this

[http://www.ubuntuforums.org/showthre...light=security]("http://www.ubuntuforums.org/showthread.php?t=9836&highlight=security")
[http://www.ubuntuforums.org/showthre...light=security]("http://www.ubuntuforums.org/showthread.php?t=98912&highlight=security") <- good debate[/QUOTE]

  I am not reading 22 pages.  What was the debates conclusion?  Do i need Anti-Virus, Anti-Spyware and Firewall?

---

### Post by kaamos on 2006-01-06
Firewall: maybe.

Do you mean you can not start synaptic or you can't find "repositories" in the menus?

---

### Post by kingsidy on 2006-01-06
antivirus = clam av
antispyware or rootkits in linux = chkroot
firewall = firestarter

all these programs are available from the repositories if u enabled your souce list.

---

### Post by byen on 2006-01-06
Ok. try this for starters:
1.Open the terminal and type :sudo gedit /etc/apt/sources.list

and copy and paste the following in there

> #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


 deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
 deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

 deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

#deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
#deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
 
Save file
Now in the terminal type:
sudo apt-get update
sudo apt-get install firestarter

thats it.. this should work as far as i can see. If you run into trouble let us know. Goodluck.

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=kaamos]Firewall: maybe.

Do you mean you can not start synaptic or you can't find "repositories" in the menus?[/QUOTE]

Can't find repositories in the menus, (had to search).  All of the other steps are not like what I am seeing on my screen.

---

### Post by Perfect Storm on 2006-01-06
[QUOTE=The Pinny Parlour]This doesn't not work:
2.3.	

How do I add Universe and Multiverse?
	

By default, Ubuntu comes pre-configured with basic and security update repositories. To enable the extra Universe and Multiverse repositories:

   1.

      Start Synaptic by selecting System->Administration->Synaptic Package Manager from the desktop menu system.
   2.

      In Synaptic choose Settings-> Repositories.
   3.

      Click the Settings button.
   4.

      Tick Show disabled software sources, then click Close.
   5.

      On the Repositories dialog box click Add. There are three separate repositories; Breezy Badger, Security Updates and Updates. Select each repository and check Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse). Ensure you click OK between each repository to save your changes.
   6.

      You should now see checkboxes next to each repository, scroll through the list and ensure they are all checked. 



There is no 'repositores' listed.
I had to search for it.
Nothing else said above is listed.[/QUOTE]


Okay, then do it manually:

```
 sudo gedit /etc/apt/sources.list

```

Remove the **#** infront of

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

and 

#deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
#deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe



then:
```
sudo apt-get update
```

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=byen]Ok. try this for starters:
1.Open the terminal and type :sudo gedit /etc/apt/sources.list

and copy and paste the following in there


Save file
Now in the terminal type:
sudo apt-get update
sudo apt-get install firestarter

thats it.. this should work as far as i can see. If you run into trouble let us know. Goodluck.[/QUOTE]
  

Is it safe to do that?

---

### Post by handy on 2006-01-06
This is worth a read, quite educational:

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

Cheers,

handy

---

### Post by Mustard on 2006-01-06
[QUOTE=The Pinny Parlour]Is it safe to do that?[/QUOTE]

Its not fatal if you make a mistake in your sources.list.  You would just go back and do it again if you make a mistake first time around.

Its actually a more common way of doing things in linux.  Doing things with graphical user interfaces is something that has only developed on linux over time.  Once upon a time it was all done via the command line.  Everyone gets familiar with it at some stage when using linux.

---

### Post by byen on 2006-01-06
If it wasnt I would have never have suggested it. It is actually a copy of my own sources.list. So go ahead and try it out. If anything goes wrong because of that.... I will personally hand you the bat and let you take a swing at me ;-)

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=byen]If it wasnt I would have never have suggested it. It is actually a copy of my own sources.list. So go ahead and try it out. If anything goes wrong because of that.... I will personally hand you the bat and let you take a swing at me ;-)[/QUOTE]

lmao:D

---

### Post by Mustard on 2006-01-06
I don't know what the last link was that you tried to learn how to use Synaptic, but you could check out these too...as they have some pictures that might help you find your way around..

[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Either that or do it manually as was shown in previous posts.  Post any questions you like in here.  it can all be a bit confusing at the start when you are learning a new operationg system.

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=Mustard]]

Either that or do it manually as was shown in previous posts.  Post any questions you like in here.  it can all be a bit confusing at the start when you are learning a new operationg system.[/QUOTE]
  Thank You   ...   Indeed it can be  :D

---

### Post by The Pinny Parlour on 2006-01-06
ok, I'm making progress.  In repositories, some say binary and some say source, do I just put a tick against all of them?   Will this open my installation of unbuntu to potential problems by not using the official programs?

---

### Post by Mustard on 2006-01-06
[QUOTE=The Pinny Parlour]ok, I'm making progress.  In repositories, some say binary and some say source, do I just put a tick against all of them?   Will this open my installation of unbuntu to potential problems by not using the official programs?[/QUOTE]

Just the binary ones is good enough.  Enabling the source is not a problem.  Its just not necessary atm.  The only way I could imagine you opening up yourself to possible problems is if you add sources that are not normally used by Ubuntu.  Multiverse and Universe are quite commonly used by ubuntu users.  The come with the default install, but are not enabled by default.

After you add the repositories, it will reload the new package lists and those new packages will appear in your Synaptic Package Manager.  All the software available in Synaptic when using the standard sources.list are safe to install.

This is an example of my sources.list

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb-src http://au.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
 deb-src http://au.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://au.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://au.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

Mine is set up to use Australian mirrors, hence the .au in the URL's.

You can view your actual sources.list by typing this command in the terminal (which is in your Applications>>Accessories menu).

```
cat /etc/apt/sources.list
```

The cat command is used for printing out the contents of text files.  The /etc/apt/ directory is where the file sources.list is stored.  Its in the 'system files' area, which is normally only editable by the administrator (thats you!), using the sudo command in front of normal commands.

---

### Post by The Pinny Parlour on 2006-01-06
[QUOTE=Mustard]

Mine is set up to use Australian mirrors, hence the .au in the URL's.

You can view your actual sources.list by typing this command in the terminal (which is in your Applications>>Accessories menu).

```
cat /etc/apt/sources.list
```

The cat command is used for printing out the contents of text files.  The /etc/apt/ directory is where the file sources.list is stored.  Its in the 'system files' area, which is normally only editable by the administrator (thats you!), using the sudo command in front of normal commands.[/QUOTE]


Thanks Mustard,  I'm Aussie too.  :)

---

### Post by jbaloul on 2007-08-09
This mite answer some of your questions...
[http://howtoforums.net/viewtopic.php?t=549](http://howtoforums.net/viewtopic.php?t=549)

JB

---

### Post by por100pre1 on 2007-08-09
> **jbaloul said:**
> This mite answer some of your questions...
[http://howtoforums.net/viewtopic.php?t=549](http://howtoforums.net/viewtopic.php?t=549)

JB

This post is very old, the original poster must be an experienced Linux user by now, and I doubt the poster have any questions at this moment.

:lolflag:

Please read before posting!

---

