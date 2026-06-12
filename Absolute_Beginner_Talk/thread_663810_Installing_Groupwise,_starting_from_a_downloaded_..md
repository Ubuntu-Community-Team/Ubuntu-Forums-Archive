---
title: "Installing Groupwise, starting from a downloaded .zip file?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Amanda T on 2008-01-10
Hi there,

This is my first post, I've had a lot of luck getting things to work by reading everyone else's problems, but this one has been giving me trouble for three days now and I've not found a good guide for my issue. If I just missed it, and you can help, please just post or send me a link, and I will be very very grateful!!!

I would very much like to run Groupwise 7 for Linux, the web based version just doesn't have the features I need, but I cannot figure out how to get it installed properly. I downloaded the .zip file from this site ([http://netstorage.loyola.edu/groupwise65/](http://netstorage.loyola.edu/groupwise65/)), and I think the best help for me right now would be straightforward walk through of how to go from this .zip file to being able to open the program through Applications. 

I tried extracting the file to a folder on my desktop, inside were two .rpm files called *novell-groupwise-gwcheck-7.0.2-20070524.i386.rpm* & *novell-groupwise-gwclient-7.0.2-20070524.i386.rpm*.  Then I went to Terminal and tried to use Alien to install the gwclient file, but I got a Warning telling me to put in --scripts, and from that point I'm lost. 

Could somebody give me a hand? I would be incredibly grateful as a college student new to this OS and pretty in need of an email client that does all I need (I worked with my IT dept on getting my account to work through Evolution, and its working only about 75%, minus some really key components for me). We start school again in about a week, and I would love to have this working by then!

Thank you in advance!! :)

---

### Post by stump138 on 2008-01-10
I've gotten the groupwise client to work in linux once before, however I'll warn you now that it isn't very high quality.  When you run the conversion in alien on the rpm package use this syntax
```
alien -c package.rpm
```

that will convert the scripts in the package as well.  Novell tends to use older libraries for their sles type applications, so don't be surprised if you come across dependency issues.

---

### Post by stump138 on 2008-01-10
in your case the code would be
```
alien -c novell-groupwise-gwcheck-7.0.2-20070524.i386.rpm
alien -c novell-groupwise-gwclient-7.0.2-20070524.i386.rpm
```

---

### Post by Amanda T on 2008-01-10
> **stump138 said:**
> in your case the code would be
```
alien -c novell-groupwise-gwcheck-7.0.2-20070524.i386.rpm
alien -c novell-groupwise-gwclient-7.0.2-20070524.i386.rpm
```

Wonderful, thank you! I will try this. So long as the program will show shared folders that I did not personally create, and I can access my college's address book, I'm all set!

Thank you again!

---

### Post by Hospadar on 2008-01-10
It looks like there are some libraries for groupwise that allow you to access it through evolution.  you might give that a try as well.

---

### Post by Amanda T on 2008-01-10
Oh boy, I hate to say this but I'm still a bit lost (sorry, I'm hitting the learning curve!).

I entered this:
 amanda@Ubuntu:~$ sudo alien -c'/home/amanda/Desktop/novell-groupwise-gwcheck-7.0.2-20070524.i386.rpm' 

And got this (plus a whole bunch of options):
Unknown option: /
Usage: alien [options] file [...]

Did I mess it up? I think the option I should use is "-d", since I need to make  a deb package so it can be installed easily, 

Also, does anyone have an idea how those two .rpm files work together? Do I need to install one first, then the other in order for it to work correctly? 

Thank you!

---

### Post by stump138 on 2008-01-10
I connect to a groupwise server using both evolution and kontact.  If they are using IMAP, you should be able to access any personalized folders, calendars etc..

---

### Post by stump138 on 2008-01-10
the -d is not needed as it will make a .deb by default, remove the space and the quotes after the -c..try cutting and pasting this :)
```
sudo alien -c /home/amanda/Desktop/novell-groupwise-gwcheck-7.0.2-20070524.i386.rpm
```

---

### Post by Amanda T on 2008-01-10
Ok, I pasted what you had, and after putting in my password, I got a blank line and nothing happened.

So I reopened Terminal to try it again (maybe I goofed), and after redo-ing it I got:

mkdir: cannot create directory `novell-groupwise-gwcheck-7.0.2': File exists
unable to mkdir novell-groupwise-gwcheck-7.0.2:  at /usr/share/perl5/Alien/Package.pm line 257.


Does this mean I DO have a .deb file somewhere? No idea what my next step is...

---

### Post by stump138 on 2008-01-10
You dont have a .deb yet, but because we've tried a few times there may be some trash you don't want lying around.  I would move the .zip to your home folder or something and then delete all references to the groupwise files.  then you can re-extract the groupwise rpm's and start fresh.

---

### Post by Amanda T on 2008-01-10
Ok, so I was cleaning off my desktop and going to move the .zip into my Home folder when I found two folders named for the two things that were in the .zip in the first place. Inside each of those folders is a folder called Debian (and a bunch of other stuff), are we on the right track? I wasn't seeing a .deb file anywhere, but I also probably don't know where to look.

Thanks again for being patient with me!

---

### Post by Amanda T on 2008-01-10
I also cannot delete either of those folders, which are actually named slightly different from the original .rpms that I first mentioned, these just have Novell-groupwise-(name)-7.0.2, if that helps indicate how they got there.

---

### Post by stump138 on 2008-01-10
OK I downloaded the same packages you have there and went through the process :)  Here are some steps you can follow:

I didn't have any of the packages extracted and the zip file sitting on my desktop. I extracted one of the .rpms to my desktop then did this in terminal
```
cd Desktop
sudo alien -c novell*.rpm
```

That created the first package.

Now delete the .rpm you have on your desktop and extract the other one to the desktop from the zip file.

Rinse and repeat the steps above and you should have 2 brand new .debs on your desktop :)

If you just want the .deb files I produced, I can make them available for download.

---

### Post by Amanda T on 2008-01-10
Fabulous! I will just try to work through the whole thing, since I really need to learn this! :-)

I'll post with the results!

---

### Post by stump138 on 2008-01-10
you'll have to be root or sudo to delete those folders

---

### Post by Amanda T on 2008-01-10
Hmm. It worked perfectly for the 'gwcheck' .deb but I ended up with only a folder for the 'gwclient', the .deb file has not shown up. Would you mind sending me the .deb for the client file? 

I assume that up next is opening the packet with GDebi and hoping it all goes smoothly from there?

Thank you again, btw.

---

### Post by stump138 on 2008-01-10
[gwclient]("http://www.montello.k12.wi.us/files/novell-groupwise-gwclient_7.0.2-20070525_i386.deb")
[gwcheck]("http://www.montello.k12.wi.us/files/novell-groupwise-gwcheck_7.0.2-20070525_i386.deb")

---

### Post by stump138 on 2008-01-10
things may or may not go smoothly from there unfortunately.  The packages you are using were developed for suse linux enterprise and there is an install script in the .zip package.  Alien just allows the conversion of the .rpm to .deb.  Whether the package actually works or not is another topic :(

---

### Post by Amanda T on 2008-01-10
Thanks!!! Now for my incredibly slow internet connection to download these guys and get them going! :-)

---

### Post by Amanda T on 2008-01-10
> **stump138 said:**
> things may or may not go smoothly from there unfortunately.  The packages you are using were developed for suse linux enterprise and there is an install script in the .zip package.  Alien just allows the conversion of the .rpm to .deb.  Whether the package actually works or not is another topic :(

Oh man, that sounds like a complete mess. If these don't work, I'm going to give up for a week and just go ask a professor at my school who has it running how they're performing this miracle. I can live via the web based version for another week.

Thank you again for all your help, have a great day!

---

### Post by pricetech on 2008-04-30
I know this is an old thread, but maybe this will help someone searching in the future.
Disclaimers:  I'm using gui tools as much as possible rather than the command line because it's simpler for new users.  Besides I'm getting too old to remember /long/drawn/out/path/and/filenames  Also, this worked for me, but may or may not work for others.  I'm not a guru, but we do have one in our IT department who's a lot of help to me on these endeavors.
Currently using Ubuntu 8.04 on a Dell GX260.

I downloaded the .gz from Novell and unzipped it using the Archive Manager.  I converted the .rpm to a .deb using alien with the -c switch, but only on the "..gwclient.." file.  (It's working, so I'm guessing that's all that's needed.)  Anyway I began with the archive extracted to my "download" folder, located within my home directory and it placed the .deb in my home directory.  I then simply double clicked on the .deb to install.
I then encounter a failure (simply wouldn't start) due to a missing library.  (libstdc++5)  which I installed using Synaptics Package Manager.
Next I got the program running, but had a blank gray screen.  (something to do with "compiz" but I haven't studied up on that one yet.)  My workaround was to turn off visual effects  (System Preferences  Appearance  Visual Effects tab)
Now it seems to be working just fine.  I have my mail as well as my Groupwise address book.

I hope this will be of some help to someone else so they don't have to "reinvent the wheel"

---

