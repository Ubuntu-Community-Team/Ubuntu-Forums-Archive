---
title: "1st attempt today... Ubuntu server, FTP..."
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by fyl2u on 2007-05-11
Hi all,

I've been given the task of researching the best way of setting up an FTP server for my workplace, a high profile recording studio in London, and have been recommended Ubuntu Server.

The alternative that's been suggested by a colleague is to get an Apple XServe and use Rumpus but a friend of mine is a networks administrator and assures me that OSX Server just isn't up to scratch.

Unfortunately, as a recording studio, we use Macs on our recording rigs and also as "surfing computers" for the main studios, and most of our clients and staff are mac owners, so it's down to me to convince them that we don't want a Mac for an FTP server. (If indeed that is the case).

The colleague of mine has already set up a G4 running Rumpus and has emailed us a link for us to click on, which allows access to the FTP site with a "nice" (debatable) GUI.

Because he's already shown the department his "results", I now have approximately 2 days to install Ubuntu Server, find and install a similar FTP system with a friendly user interface and be able to demonstrate it as being easy to use and maintain.

Did I mention I have very little experience with Linux (have only ever used it to surf the net on a friend's machine a few months ago for half an hour and have never attempted an install)?

I'm not completely computer illiterate, though.  I did A-Level computing back in 91-93 and even did the first year of a computing degree (before deciding I wanted to be a musician instead of a programmer after realising I was further up the "skill field" for that career direction).  My point being, I do have a history of programming in various languages (from Basic on the Speccy/A464 when I was a nipper through to Pascal, C+, ADA etc at college/uni and HTML in more recent times), although I haven't done any serious programming in years.

One other sticking point for my side of the debate is the support infrastructure.  My supervisor is concerned (to say the least) that going in the Linux direction means that there's no "official" line of support and that he would require something more "solid" (like the support he thinks he'd get from Apple, although from my experience with Applecare I severely doubt they could help me sort out FTP server install problems).

Can anyone advise me on any of these points?

Am I dreaming on the 2 day timeframe?

Is there a piece of friendly gui-based web-page-style non-install-requiring software (equivalent to Rumpus) so that they don't have to install client software or use Fetch / Cyberduck etc (which is too difficult for many of our clients it seems :roll: )

Thanks in advance,

Phil

---

### Post by fyl2u on 2007-05-11
Anyone?

---

### Post by llamakc on 2007-05-11
You need to be patient. Have you tried researching FTP servers yet? After installing it's as simple as using any of the package management front ends to install the ftp server of your choice.

Here's how I would do it: install Ubuntu server. When that was over, type:

sudo apt-get install proftpd

Voila! Done. From there how it is set up will depend on YOUR needs. As I am unaware of Mac's FTP clients I can't make any suggestions. Doesn't the o/s have the ability to browse FTP servers on it's own?

How do you want the ftp server set up? Are users connecting to a global share? or their user shares?

---

### Post by fyl2u on 2007-05-11
Sounds very easy to set up the FTP server side of things.

The alternative system for Mac, "Rumpus" just runs in any browser, so the recipient just clicks a link and they're in.  It looks quite pretty and more importantly is easy for the recipient to access.

(Believe it or not, some of our FTP recipients seem to have great difficulty accessing out FTP site using 3rd party FTP client software like Fetch etc.).

My colleague already has Rumpus up and running on a G4 at his house on a standard ADSL line.

Is there an equivalent for Ubuntu, where we could just email a link to a recipient, who could then just click a "download files" button from his browser (regardless of their own platform - XP, Mac or other) without needing to install any FTP software?

As for the setup of the server, ideally we could have a small number of access folders so that any one recipient could not access files that are intended for another recipient.  We don't need hundreds... 4 or 5 passworded folders would probably be sufficient.

---

### Post by louieb on 2007-05-11
From firsthand experience in setting up an FTP server on my small home network  it was easy. Get the server CD, install it on a machine, install proftpd,  set up the network connection to use a static IP, set up Users. 
An ftp server for a business should have the same steps only real difference is the number of users.  As for support try     [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

---

### Post by fyl2u on 2007-05-11
OK.... 2 downloads of Server Edition 7 and 4 blank CDs later and I'm no closer to getting it installed.

I've blamed the first 2 failures on cheap CDs, the 3rd (on a £10 high quality CDR) on burning the disk too quickly, but the 4th one was (...also on a £10 high quality CDR and...) done at 8x... could it be a glitch in my download?  It was coming down at around 500kps, which I have to say I was very impressed at.

Anyway, I've decided to give up on v.7 for now and try to get going on v.6
(unless someone can convince me that I should just try to DL it again but it's costing me a lot of money in CDs, using these £10 disks).

---

### Post by fyl2u on 2007-05-11
Actually, I've changed my mind again.

After reading another thread I've decided to go for the desktop edition v.7

---

### Post by UltimaDude on 2007-05-11
What CD's you using, you could try the TDK CDR's they work great with Ubuntu.

---

### Post by hyper_ch on 2007-05-11
What kind of access do you need exactely?

Shall people from outside the business network be able to up/download?
What about authorisation?
...
...

---

### Post by Wim Sturkenboom on 2007-05-11
Maybe a silly comment, but Dapper Drake (6.06) will be supported for a longer time than V7. And that's important in professional environments.

---

### Post by fyl2u on 2007-05-11
> **Wim Sturkenboom said:**
> Maybe a silly comment, but Dapper Drake (6.06) will be supported for a longer time than V7. And that's important in professional environments.

I noticed that on the download page... why is that?  Isn't the later version "better"?

I'm having a go with V7 desktop (done at 4xspeed) now - just checking the cd for errors now.

---

### Post by fyl2u on 2007-05-11
> **hyper_ch said:**
> What kind of access do you need exactely?

Shall people from outside the business network be able to up/download?
What about authorisation?
...
...

Yes, we'll be transferring huge files/folders across the world to/from people from other organisations (mastering houses, bands, other studios, producers, A&R etc.)

It needs to be ultra secure (so that people don't steal the latest albums/songs from us before they're finished / released) but we'd only need 4 or 5 separate passworded folders, max.

Authorisation?

---

### Post by fyl2u on 2007-05-11
> **UltimaDude said:**
> What CD's you using, you could try the TDK CDR's they work great with Ubuntu.

These are HHB "Pro Recording Media - For Critical Audio And Data Applications".

---

### Post by fyl2u on 2007-05-11
Yay - no errors found... looks hopeful.

---

### Post by echo $USER on 2007-05-11
vsftpd is a nice ftp service as well...

sudo apt-get install vsftpd

But if its important stuff, you might want to look into secure copy over ssh.

---

### Post by hyper_ch on 2007-05-11
have a look here:

[http://www.howtoforge.com/taxonomy_menu/1/35](http://www.howtoforge.com/taxonomy_menu/1/35) - the tutorials for Debian should also work for Ubuntu

---

### Post by fyl2u on 2007-05-11
> **echo $USER said:**
> vsftpd is a nice ftp service as well...

sudo apt-get install vsftpd

But if its important stuff, you might want to look into secure copy over ssh.

vsftpd?

Does it have a browser-based front end for the downloader?  That's quite important, as some of our recipients seem to have trouble using 3rd party FTP client software.  They just want to click on a link and press a button to download a file.

---

### Post by dca on 2007-05-11
You could use gFTP if you're looking for a GUI-based FTP utility or Firefox for browser-based.  I would recommend using Ubuntu 6.06LTS (I bet people are getting tired of hearing me recommend it) for its stability and long term support (security updates, etc) versus Feisty or Edgy.  Using Ubuntu versus Debian (which is what it's based on) or even and RPM-based distro eliminates a lot of the bloat 1CD versus 24 or 6 for the RPM-based distros...  Depolyability, w/ installation and post-config is incredible.  As mentioned above you can use 'vsftp' for the ftp service...
 
 
All right, I'm done, I sound like a commercial now...

---

### Post by dca on 2007-05-11
Sorry, to answer the other question, if you configure the 'vsftpd.conf' file to:  not allow anonymous, reconfig ftp group id/user id, etc, etc...  The user accessing through a web browser should (after putting [ftp://yaddayaddayadda.com](ftp://yaddayaddayadda.com) in the browser) be shown a login window...
 
 
The way I did my boxes was I installed both Samba and vsftp on them...  I would migrate the files from a Windows box to the server via Samba and others (remotely, different locations, etc) would access via FTP...

---

### Post by fyl2u on 2007-05-11
> **echo $USER said:**
> vsftpd is a nice ftp service as well...

sudo apt-get install vsftpd

But if its important stuff, you might want to look into secure copy over ssh.

OK, I've just typed this into the terminal and it says it's done it, but I can't see any reference to it anywhere but in the terminal window at the moment... sorry for being such a noob, this really is my first foray into trying anything clever with a linux machine.

---

### Post by fyl2u on 2007-05-14
OK - I'm working at a different site today, so they're supplying me with another computer of the same spec to try and get going as a VSFTP server.

I'm feeling more confident today, after my first evening's exploits in Ubuntuland on Friday.

Thanks everyone for your help.  You may very well see a few more requests on here today :oops:

---

### Post by fyl2u on 2007-05-14
Hmmmn... strange... I'm sure it installed faster than this on Friday.


I booted from the CD, double-clicked the "install" icon, and it started accessing the CD.

3 or 4 minutes later a window has popped up that says "install" in the bar at the top, has the minimise, maximise and close buttons, but the pane is completely white.

The numlock and caps lock keys are no longer responding and neither is the mouse pointer, and it just keeps accessing the CD for ages (half an hour now, at least), occasionally going all quiet until I shake the mouse.

Is it failing or is it supposed to be like this?

I'm pretty sure it didn't do this on Friday with an identical machine. :-?

---

### Post by fyl2u on 2007-05-14
actually, when I say the mouse isn't responding, it *is*, but with a 30 second lag.

---

