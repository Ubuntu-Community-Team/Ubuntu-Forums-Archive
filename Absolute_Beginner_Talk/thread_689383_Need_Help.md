---
title: "Need Help"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by whiskysmuggler on 2008-02-06
I run a Real Estate business. I have no knowledge of Command Line entries. In other words
I'm lost.
I have dumped my Vista in lieu of Ubuntu 7.10. I like the enviornment and the small footprint.
My problem is that one of the tools that my company uses (and it is mandatory) will only operate in IE 6 or better.
Who can guide a dummy like me thru the process of install?
Thanks in advance to all help
Peace, Whisky

---

### Post by aquavitae on 2008-02-06
So it doesn't work in firefox?  What is the tool - something common you might find an alternate to or something custom made for your company? Ideally, you should try to persuade the developers of the tool to support other browsers (e.g. firefox).

Installing IE6 in linux is not a simple task, if its even possible! You might be able to do something with wine ([www.winehq.org](www.winehq.org)) but otherwise I'd suggest you install winxp in a virtual machine  and use the tool through that.  This would be the easier option.  To do this, install virtualbox (from the repos), and when you run it, you should be able to install winxp in it.

Don't know how much of that you understand... :)

---

### Post by seventhc on 2008-02-06
Are you sure it isn't just plugins that you need???

---

### Post by mangurt on 2008-02-06
I use ie4linux

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Click on the link, follow the instructions.  I have to use IE for somethings, and this was a true lifesaver.

Hope this helps you.

---

### Post by whiskysmuggler on 2008-02-06
aqavite, hope I spelled that correctly...
Yes, I get the Idea of VM...but where do I find it. Did not locate on the add/remove from applecations.
I quit windows because of the way they hogged disk space with updates. So Linux/Ubuntu is totaly new to me.
I have played with computers since 85, so even though I am a novice, I am not completely stupid.
Ubuntu would not load under MSFT's VM, in retrospect I hope that Windows will load under Ubuntu's version.
The program I must use is a service I subscribe to as a Realtor. I have already complained about their not running in Linux/Ubuntu, but I am a small minority in that end and will not get any satisfaction for some years.
Thank you for your help...

Peace, Whisky

---

### Post by whiskysmuggler on 2008-02-06
Not a plug in. Firefox is good about providing info on plugins neede.  Support from service says I need IE 6 or better to run their app.
No support from them as how to accomplish this.
Thank You, 
Peace, Whisky

---

### Post by emarkd on 2008-02-06
> **mangurt said:**
> I use ie4linux

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Click on the link, follow the instructions.  I have to use IE for somethings, and this was a true lifesaver.

Hope this helps you.

I second this suggestion.  I do some web development and need IE for testing and this project works great.  And it's very easy to get installed and going.

Skip Wine on this one and do it this way!

---

### Post by whiskysmuggler on 2008-02-06
Mangurt...thamks, this looks like the solution.
I did state I am a novice. I am in termanal default launch. How do I change directories to enable me to follow directions?
Thanks for your help;
Peace, Whisky

---

### Post by emarkd on 2008-02-06
Are you using these directions:  [http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)  Just type in what they say there.

If you need to change directories, you just issue a 'cd directoryname' but those directions look pretty complete.  If you have any specific problems, just ask and we'll try to help.

---

### Post by aquavitae on 2008-02-06
I agree, ie4linux is probably a better solution - I'd forgotten about it!

If you do want to try a virtual machine, Virtualbox is in the repos (just checked) and it should do it.  I had no problems getting winxp working in linux, as for the other way round.... about 3 months!  And in the end it was virtualbox (for windows) that did it.

---

### Post by whiskysmuggler on 2008-02-06
Ok, back to DUMMIE (-"
I went to terminal and typed the first line  I got [sudo]  password for 

So I must need to change directories. the old dos cd does not seem to work, or I have forgotten the procedure, it has been years.
Again, thank you, Whisky

---

### Post by emarkd on 2008-02-06
What error did you get on that first line?  You don't have to 'cd' to make that work because the command takes into account the entire path to the file.  

'cd' is for change directory, by the way, but you don't have to use it for this step.

---

### Post by aquavitae on 2008-02-06
cd does work, but there must be a space after it (i.e. cd.. won't work, cd .. will) and remember to use / instead of \.

---

### Post by seventhc on 2008-02-06
are you following from this? [http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)
you can just copy and paste, or highlight the line needed then middle click in the terminal. :)

---

### Post by mangurt on 2008-02-06
Yeah, open terminal and cut and paste the directions from the link.  I have to use IE because I am in the reserves, and all the sites are internet only sites.  The works like a champ.

---

### Post by whiskysmuggler on 2008-02-07
I want to thank everyone who helped me with this post.
Like I said, I'm a newvbie...It took a while to sink in...but what a system. Once I figured out what everyone was telling me to do, what a snap. Cool
Again thanks for all the help.

Peace, Whisky

---

### Post by emarkd on 2008-02-07
You're welcome.  Glad you got it working.  If you want to get more comfortable with the command line, and learn a lot about your new operating system, [here's]("http://linuxcommand.org/") a good link.

---

### Post by whiskysmuggler on 2008-02-12
Ok, thought we had this all figured out...not. When I'd log into my business acct. the page would still not display. I've played with this for over a week now and getting nowhere. Followed all steps ffom provided link and re-run entire process. Wine and cab extractor are installed properly.  ies4Linux is what is hanging up. Here are the last few lines of the download.  Any idias?


ies4linux-2.99.0.1/ui/.svn/tmp/prop-base/
ies4linux-2.99.0.1/ui/.svn/tmp/text-base/
ies4linux-2.99.0.1/ui/.svn/tmp/props/
ies4linux-2.99.0.1/ui/pygtk/python-gtk.sh
ies4linux-2.99.0.1/ui/pygtk/ies4linux-gtk.py
ies4linux-2.99.0.1/ui/kommander/advanced.kmdr
ies4linux-2.99.0.1/ui/kommander/kommander.sh
ies4linux-2.99.0.1/ui/kommander/logo.kmdr
ies4linux-2.99.0.1/ui/kommander/installation.kmdr
paddy@paddy-desktop:~$ cd ies4linux-*
paddy@paddy-desktop:~/ies4linux-2.99.0.1$ ./ies4linux


Thanks, Paddy:guitar:
Xlib: unexpected async reply (sequence 0x104b)!

---

### Post by whiskysmuggler on 2008-02-12
Sorry, missed the last 2

ies4linux-2.99.0.1/ui/kommander/installation.kmdr
paddy@paddy-desktop:~$ cd ies4linux-*
paddy@paddy-desktop:~/ies4linux-2.99.0.1$ ./ies4linux
Xlib: unexpected async reply (sequence 0x104b)!


:guitar:

---

