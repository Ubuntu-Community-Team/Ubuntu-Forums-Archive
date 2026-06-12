---
title: "gnomebaker and multisession?"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-04-13
Hi all! I read somewhere that gnomebaker will allow multisession (data) recording, If so what is the process to achieve this?
Thanks

---

### Post by Mustard on 2006-04-13
[QUOTE=Sbarton]Hi all! I read somewhere that gnomebaker will allow multisession (data) recording, If so what is the process to achieve this?
Thanks[/QUOTE]

That's a good question. I can't see the options anywhere in the interface, nor does the manual clarify the situation, other than saying that it is supported.

---

### Post by korami on 2006-04-14
Well, as far as I experienced, the default burning mode in GnomeBaker is actually multisession, and you have to choose probably disk-at-once writing mode to avoid multisession.

---

### Post by Sbarton on 2006-04-14
[QUOTE=korami]Well, as far as I experienced, the default burning mode in GnomeBaker is actually multisession, and you have to choose probably disk-at-once writing mode to avoid multisession.[/QUOTE]
Thanks for the reply, I tried this but I see no option for 'disk-at-once'. I burnt a data file, ejected tried to burn another one to see if the default was for multisession. It went through its procedure exactly the same. However, when checking the disc, no other file was burnt to it. Have you done a multisession? If so could you let me know how this is done?
Thanks

---

### Post by Sbarton on 2006-04-15
Sorry to bump my own post, but I was still wondering if anyone knows for sure if Gnomebaker is a 'multisession' burning software. As previously mentioned it does state it is supported, but how does it work if it is? It does not seem to default to multisession and there are no options to choose from. If it is not does anyone know of a multisession software?
Regards

---

### Post by korami on 2006-04-15
[QUOTE=Sbarton]Thanks for the reply, I tried this but I see no option for 'disk-at-once'. I burnt a data file, ejected tried to burn another one to see if the default was for multisession. It went through its procedure exactly the same. However, when checking the disc, no other file was burnt to it. Have you done a multisession? If so could you let me know how this is done?
Thanks[/QUOTE]

This might have happened in case you didn't import the previous session. So here are the steps I follow for writing a multisession disk with GnomeBaker:

**1st Session:**
1. Add Files to Data Disk
2. Create data disk. Mode="default" or "tao" (default should be tao, i.e. track-at-once).
3. Start
4. Ok.

**Next session:**
1. **Import** the previous session(s) (Import button). You might have to unmount the disk manually in case you get errors at importing the disk (apparently GnomeBaker can't handle very well the unmounting of a mounted CD)
2. Add Files to Data Disk
3. Create data disk. Mode="default" or "tao" (default should be tao, i.e. track-at-once).
4. Start
5. Ok.

And that's it. You should have now a multisession disk.

I agree though that this option should be user-friendlier, and one should be able to explicitly select "multisession" or "no multisession". I also don't know how one ends a multisession, but I can live with it.

---

### Post by steve.horsley on 2006-04-15
[QUOTE=Sbarton]Sorry to bump my own post, but I was still wondering if anyone knows for sure if Gnomebaker is a 'multisession' burning software. As previously mentioned it does state it is supported, but how does it work if it is? It does not seem to default to multisession and there are no options to choose from. If it is not does anyone know of a multisession software?
Regards[/QUOTE]
Maybe you should try k3b. It has an option for multisession, and I seem to remember it easily adds to a part-filled multisession. It is the most reliable burner I have ever used on Linux, and has more options than I can cope with. Fortunately, the defaults are all very sensible.

---

### Post by Sbarton on 2006-04-15
[QUOTE=steve.horsley]Maybe you should try k3b. It has an option for multisession, and I seem to remember it easily adds to a part-filled multisession. It is the most reliable burner I have ever used on Linux, and has more options than I can cope with. Fortunately, the defaults are all very sensible.[/QUOTE]

OK! Many thanks for that Steve.:)

---

### Post by Sbarton on 2006-04-16
[QUOTE=steve.horsley]Maybe you should try k3b. It has an option for multisession, and I seem to remember it easily adds to a part-filled multisession. It is the most reliable burner I have ever used on Linux, and has more options than I can cope with. Fortunately, the defaults are all very sensible.[/QUOTE]

Steve where is the option for multisession in K3b?
Thanks, regards.

---

### Post by htinn on 2006-04-16
The "Import" button is right next to the "Burn" button in K3b.

---

### Post by Sbarton on 2006-04-16
[QUOTE=korami]This might have happened in case you didn't import the previous session. So here are the steps I follow for writing a multisession disk with GnomeBaker:

**1st Session:**
1. Add Files to Data Disk
2. Create data disk. Mode="default" or "tao" (default should be tao, i.e. track-at-once).
3. Start
4. Ok.

**Next session:**
1. **Import** the previous session(s) (Import button). You might have to unmount the disk manually in case you get errors at importing the disk (apparently GnomeBaker can't handle very well the unmounting of a mounted CD)
2. Add Files to Data Disk
3. Create data disk. Mode="default" or "tao" (default should be tao, i.e. track-at-once).
4. Start
5. Ok.

And that's it. You should have now a multisession disk.

I agree though that this option should be user-friendlier, and one should be able to explicitly select "multisession" or "no multisession". I also don't know how one ends a multisession, but I can live with it.[/QUOTE]

I know this is inexcusable but somehow I totally missed this post. I think I must have gone to the last post by-passing yours. Very sorry for that! I will try that. Once again my apologies!
Regards.

---

### Post by korami on 2006-04-16
[QUOTE=Sbarton]I know this is inexcusable but somehow I totally missed this post. I think I must have gone to the last post by-passing yours. Very sorry for that! I will try that. Once again my apologies!
Regards.[/QUOTE]

No prob. I just hope you'll get along.

I also agree with Steve that k3b is far more advanced, but using Gnome as desktop environment, I like to stick to Gnome apps. k3b is the next choise however when something goes wrong with GnomeBaker.

---

### Post by Sbarton on 2006-04-17
[QUOTE=korami]No prob. I just hope you'll get along.

I also agree with Steve that k3b is far more advanced, but using Gnome as desktop environment, I like to stick to Gnome apps. k3b is the next choise however when something goes wrong with GnomeBaker.[/QUOTE]

I did try, but as you mentioned there probably was a unmount problem. I also agree with you in trying to keep to gnome apps. However, I did use k3b and it worked perfectly, so I can now continue with multisessions. Thanks to everyone who posted for your input. Much appreciated!
Regards

---

### Post by Sbarton on 2006-04-17
I thought I would add one other point as regards the unmount. K3b seems to unmount automatically (nifty) and makes the whole excercise easy. So start/importsession/and then add other files and then burn, GREAT! Easy Peasy!!
Regards and THANK YOU!!

---

### Post by jayseye on 2007-12-13
GnomeBaker 0.6.2 under Ubuntu 7.10 (Gutsy Gibbon) can create the first session, but subsequently fails to import that session, reporting "Error getting information / unknown error" in a dialog box. 
 
The error occurs regardless of whether the CD is mounted; in fact, GnomeBaker will successfully unmount the CD when trying to import the session. However, the error occurs even if the CD is umounted manually before starting up GnomeBaker. 
 
K3b is able to import the first session from the same CD, so this appears to be a GnomeBaker import bug. Their website list multisession support under future options. Posts on the GnomeBaker forums seem to go unanswered for years. 
 
I love K3b, or could even use xcdroast for much less overhead, but would prefer a GNOME-based program like GnomeBaker when running standard Ubuntu. So: 
 
Has anyone here seen and solved this issue under Gutsy, or can someone recommend an alternative, GNOME-based burning program which correctly handles multisession CDs? 
 
Thanks! 

> **korami said:**
> 

**Next session:**
1. **Import** the previous session(s) (Import button). You might have to unmount the disk manually in case you get errors at importing the disk (apparently GnomeBaker can't handle very well the unmounting of a mounted CD)
2. Add Files to Data Disk
3. Create data disk. Mode="default" or "tao" (default should be tao, i.e. track-at-once).
4. Start
5. Ok.
 


---

### Post by jayseye on 2007-12-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnomebaker/+bug/176149](https://bugs.launchpad.net/ubuntu/+source/gnomebaker/+bug/176149) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
 
Two quick follow-ups to my previous post: 
 
First, I filed a bug report for this issue (as noted above). 
 
Second, I've tested Brasero and found that, despite some minor bugs and quirks, it works for multisession CDs. :cool:

---

### Post by Pygi on 2007-12-13
Hello,

first of all, nice to see people discussing bugs and the potential ways to solve them.
Let's play. As you probably know, as of Gnomebaker 0.6.2 initial support for multiple backends has been implemented. What backend are you using?

You can see that in the preferences dialog. If you're using cdrkit, would you be so kind
to use cdrtools backend (You need cdrtools installed for that), or vice versa?
That would help me a lot, and I'll look over that bug somewhere tomorrow to hopefully
get more insight into what's happening.

On a similar note ... I might be missing something, but I think I closed forums and website some time ago? :)

Who knows, perhaps I can do a new bugfix release if we fix this? :)

KR,
M.

---

### Post by jayseye on 2007-12-14
Thanks for the quick reply, Pygi - 
 
I will definitely re-install Gnomebaker if that would help you to trace and fix this issue. First I'll clarify that the bug occurred using the default Gnomebaker settings on a clean install of Ubuntu Gutsy Gibbon. Then installed Gnomebaker as my first program, using Synaptic. Might that answer your question about which (default) backend was used? 
 
I discovered Gnomebaker yesterday by searching UbuntuForums for "multisession," so this is my first exposure to the program. After reporting the bug, I used Synaptic to Remove it Completely, along with its "Automatic" dependencies, before installing Bracero. Took this action after noting that support for the Gnomebaker project seemed inactive, per the tracker items (Public Areas) on its SourceForge project page, at: 
 
 [http://sourceforge.net/projects/gnomebaker](http://sourceforge.net/projects/gnomebaker) 
 
The impression of inactivity was reinforced by the fact that the listed project Website also was unavailable. If you intend to keep the project alive, though, then I apologize for jumping to conclusions, and will be glad to help in any way possible. 
 
Would you like me to uninstall Bracero and reinstall Gnomebaker? Or can you easily reproduce the issue on a clean install of Ubuntu 7.10 Desktop? 
 
Thanks again, 
jayseye

---

### Post by stchman on 2007-12-14
> **Sbarton said:**
> Hi all! I read somewhere that gnomebaker will allow multisession (data) recording, If so what is the process to achieve this?
Thanks

I find that Gnomebaker is just a quick and dirty CD/DVD burner.  K3B is far more featured, I recommend using it over Gnomebaker.

---

### Post by Pygi on 2007-12-15
> **jayseye said:**
> Thanks for the quick reply, Pygi - 
 
I will definitely re-install Gnomebaker if that would help you to trace and fix this issue. First I'll clarify that the bug occurred using the default Gnomebaker settings on a clean install of Ubuntu Gutsy Gibbon. Then installed Gnomebaker as my first program, using Synaptic. Might that answer your question about which (default) backend was used? 
 
I discovered Gnomebaker yesterday by searching UbuntuForums for "multisession," so this is my first exposure to the program. After reporting the bug, I used Synaptic to Remove it Completely, along with its "Automatic" dependencies, before installing Bracero. Took this action after noting that support for the Gnomebaker project seemed inactive, per the tracker items (Public Areas) on its SourceForge project page, at: 
 
 [http://sourceforge.net/projects/gnomebaker](http://sourceforge.net/projects/gnomebaker) 
 
The impression of inactivity was reinforced by the fact that the listed project Website also was unavailable. If you intend to keep the project alive, though, then I apologize for jumping to conclusions, and will be glad to help in any way possible. 
 
Would you like me to uninstall Bracero and reinstall Gnomebaker? Or can you easily reproduce the issue on a clean install of Ubuntu 7.10 Desktop? 
 
Thanks again, 
jayseye

Hello,

if Brasero works for you, by all means use it. Phillipe and Luis are doing good work on it. Anyway, by default Gutsy comes with cdrkit, and without cdrtools, so Gnomebaker would use it. If you install cdrtools, you should get an option to use it in preferences dialog. Please try it if you wish, and tell me the result. You don't have to uninstall Brasero to install Gnomebaker. I'll also have a look at the logs if they are attached to LP's bug, and as soon as I can get some time test myself as well.

KR,
M.

---

### Post by Pygi on 2007-12-15
> **stchman said:**
> I find that Gnomebaker is just a quick and dirty CD/DVD burner.  K3B is far more featured, I recommend using it over Gnomebaker.

Gnome and KDE applications share different paradigm of approach to features and users, and this can be seen in comparison of any application which try to solve similar problems. That said, if you use Gnome, you'll ofcourse have more integration of Gnome apps into the system then you'll have it with KDE application. 

Ofcourse, K3b is a great application and Sebastian is doing great work on it. If you prefer it over Gnomebaker, Brasero or any other similar application, please do use it.

In the end, it all comes down to what rocks your boat.

KR,
M.

---

### Post by jayseye on 2007-12-19
Thanks for the follow-up, Pygi - 
 
Import Session works only after manually editing the "Mount point" field, in the dialog from Edit > Preferences > Devices. Yes, the fields are editable, and in my case the appropriate value was "/media/cdrom1" per this relevant line from /etc/fstab : 
 
 /dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0 
 
and this one from /etc/mtab : 
 
/dev/scd1 /media/cdrom1 iso9660 ro,nosuid,nodev,user=marc 0 0 
 
I got the same result regardless of which Backend was chosen. As background info: 
 
Reinstalled Gnomebaker because Brasero only seems able to *-continue-* an existing multisession CD-R; it fails to *-begin-* creating the first session of a multisession CD, at least when burning from an .ISO image. 

Then confirmed that "Wodim" is reported as Gnomebaker's Backend, corresponding to cdrkit, as you wrote. 
 
Since Synaptic lacks the "cdrtools" package under Gutsy, I installed "cdrecord" and "mkisofs" as separate packages. Was then able to choose "cdrecord" as Gnomebaker's Backend, and to successfully burn an initial session to CD from an .ISO image file. (This also worked with Wodim selected.) 
  
Gnomebaker still failed to Import Session, reporting: "The mount point (e.g. /mnt/cdrom) for the writing device could not be obtained.  Please check that the writing device has an entry in /etc/fstab and then go to preferences and rescan for devices." 
 
Following those instructions has no effect because Gnomebaker fails to show the mount point even after rescanning for devices, and it unmounts the CD when the user chooses Import Session. 
 
Manually editing the "Mount point" does allow Import Session to work, but I've yet to actually burn a second session. The need for that should come up again soon; or I could go ahead and burn one if that would help you to trace the issue(?).  
 
However, I assume that this workaround will help point you in the right direction. Please let us know here! 
  
Thanks again, 
jayseye 
 
 
> **Pygi said:**
> Hello,

if Brasero works for you, by all means use it. Phillipe and Luis are doing good work on it. Anyway, by default Gutsy comes with cdrkit, and without cdrtools, so Gnomebaker would use it. If you install cdrtools, you should get an option to use it in preferences dialog. Please try it if you wish, and tell me the result. You don't have to uninstall Brasero to install Gnomebaker. I'll also have a look at the logs if they are attached to LP's bug, and as soon as I can get some time test myself as well.

KR,
M.

---

### Post by Pygi on 2007-12-19
First of all, thank you for taking the time to do some testing. I really appreciate it.
I know that from older days Gnomebaker wears nasty bugs when it comes to device detections, and some time ago I did some work to move that  part to libburn (since I never
had the time to actually port entire app to use it), and that worked really well. Perhaps I should revive that pieces ... hm, who knows. Anyone wants to help in Gnomebaker development? :)

KR,
M.

---

### Post by jayseye on 2007-12-19
You're welcome for the testing - 
 
I also decided to test writing a second session, using Dummy Write. That failed, with different symptoms for each Backend: 
 
With Wodim, Gnomebaker slowed down to a crawl and finally had to be Force Quit. With cdrecord, it reported a problem accessing /dev/sg1 and stopped gracefully. I quit at that point, assuming that these quirks have already been reported elsewhere; but could get more information (logs) if that would help. 
 
It is possible to create and append multisession CDs by using both Gnomebaker and Brasero, since their working features are complementary. However, that's a lot to ask of a typical Ubuntu user. From that naive viewpoint, it would seem that the two projects should be combined to get one solid program with a full set of features. 
 
So, can you give a brief overview of the history, intentions and plans for Gnomebaker, in relation to Bracero? For instance, why did you close the website and forums, as mentioned in an earlier post here? Are you looking for help, or for someone to take over the project? Why is Bracero labelled as being supported by Ubuntu, while Gnomebaker is not? Has either project considered using code or techniques from working programs like xcdroast or k3b? 
 
Personally I do use k3b in KDE on Slackware Linux, ever since switching from GNOME-based RedHat 5.x. Today, if Kubuntu were the mainline brand, I'd ignore its poor relation, GNOME-based Ubuntu, without a second thought. But due to Ubuntu's tremendous popularity with users and developers, and especially its large package library, that's the direction I need to take my consulting & support business. 
 
So I'm eager to learn how GNOME has matured, and would like to find apps which fit seamlessly into the Ubuntu desktop. Though part of me would love to give up and use k3b, I'm hoping that Gnomebaker and/or Bracero will develop as a serious contender. If that requires my help with coding or, more likely, testing, then so be it. First I need to know where these projects are coming from, and where they'd like to go. 
 
Thanks for bearing with me, 
jayseye

> **Pygi said:**
> First of all, thank you for taking the time to do some testing. I really appreciate it.
I know that from older days Gnomebaker wears nasty bugs when it comes to device detections, and some time ago I did some work to move that  part to libburn (since I never
had the time to actually port entire app to use it), and that worked really well. Perhaps I should revive that pieces ... hm, who knows. Anyone wants to help in Gnomebaker development? :)

KR,
M.

---

### Post by Pygi on 2007-12-19
> **jayseye said:**
> You're welcome for the testing - 
 
I also decided to test writing a second session, using Dummy Write. That failed, with different symptoms for each Backend: 
 
With Wodim, Gnomebaker slowed down to a crawl and finally had to be Force Quit. With cdrecord, it reported a problem accessing /dev/sg1 and stopped gracefully. I quit at that point, assuming that these quirks have already been reported elsewhere; but could get more information (logs) if that would help. 
 
It is possible to create and append multisession CDs by using both Gnomebaker and Brasero, since their working features are complementary. However, that's a lot to ask of a typical Ubuntu user. From that naive viewpoint, it would seem that the two projects should be combined to get one solid program with a full set of features. 
 
So, can you give a brief overview of the history, intentions and plans for Gnomebaker, in relation to Bracero? For instance, why did you close the website and forums, as mentioned in an earlier post here? Are you looking for help, or for someone to take over the project? Why is Bracero labelled as being supported by Ubuntu, while Gnomebaker is not? Has either project considered using code or techniques from working programs like xcdroast or k3b? 
 
Personally I do use k3b in KDE on Slackware Linux, ever since switching from GNOME-based RedHat 5.x. Today, if Kubuntu were the mainline brand, I'd ignore its poor relation, GNOME-based Ubuntu, without a second thought. But due to Ubuntu's tremendous popularity with users and developers, and especially its large package library, that's the direction I need to take my consulting & support business. 
 
So I'm eager to learn how GNOME has matured, and would like to find apps which fit seamlessly into the Ubuntu desktop. Though part of me would love to give up and use k3b, I'm hoping that Gnomebaker and/or Bracero will develop as a serious contender. If that requires my help with coding or, more likely, testing, then so be it. First I need to know where these projects are coming from, and where they'd like to go. 
 
Thanks for bearing with me, 
jayseye

Is cdrecord installed suid root? Schilly seems to advise that seems to be problem with accessing the drive. Brasero is a moving target right now, and a lot of changes are being done, especially with the plugin interface and scsi changes which can be previewed in Brasero 0.6.90. I have no idea which one is in Gutsy right now.

I'm not the founder of the Gnomebaker project, but am it's current maintainer. Gnomebaker wears a lot of ugly code (especially GTK+ related one) and in general I don't like the cdrecord/cdrkit backends. I would much more prefer having a solid application based on top of libburnia libraries (libburn, libisofs, libisoburn) with a particular focus on accessible UI based on users research and input. I'd also like input on features which should be there. Too bad there's not too much interest among people to help with developing that.

Plans for Gnomebaker you ask? Basic maintaince and fixing high-profile bugs, at least now when I'm alone on the project. Forums began getting spam, and nobody wanted to took time to help there and on the website. Help? Help is always more then welcome.
Who labelled Brasero as being supported by Ubuntu, and Gnomebaker not? I really don't get this. As I said, if I had a chance to choose, my look would be towards libburnia project for backend ([http://libburnia-project.org](http://libburnia-project.org)), given I'm it's lead developer and I know it's strenghts and technical advantages. You can find my email on libburnia page ... mail me with your jabber ID, and we'll talk more.

KR,
M.

---

### Post by goedson on 2007-12-19
> **Pygi said:**
> 
Who labelled Brasero as being supported by Ubuntu, and Gnomebaker not?


I believe the reason he sees it this way is because brasero is in main (since Gutsy) and gnomebaker is in universe.

---

### Post by stchman on 2007-12-19
> **Pygi said:**
> Gnome and KDE applications share different paradigm of approach to features and users, and this can be seen in comparison of any application which try to solve similar problems. That said, if you use Gnome, you'll ofcourse have more integration of Gnome apps into the system then you'll have it with KDE application. 

Ofcourse, K3b is a great application and Sebastian is doing great work on it. If you prefer it over Gnomebaker, Brasero or any other similar application, please do use it.

In the end, it all comes down to what rocks your boat.

KR,
M.

No, it really comes down to what works and what does what I want.  K3B does more than Gnomebaker.  It does not matter that it is a KDE app or what.  Just because I use Gnome as my desktop does not mean I HAVE to use Gnome apps.  This is the beauty of Linux...choice.  If one app does not do what you need, then you can use another.

---

### Post by jayseye on 2007-12-20
I appreciate the detailed reply about both projects, and have responded privately as you requested. 
 
The short, relevant answer here is that cdrecord is indeed installed suid root (octal mode 4755) by Gutsy. Might turning off the suid bit have adverse effects, such as requiring that Gnomebaker be run as root via su or sudo? 
 
> **Pygi said:**
> Is cdrecord installed suid root? Schilly seems to advise that seems to be problem with accessing the drive...

---

