---
title: "[SOLVED] Black Screen - Is it GNOME or is it NOMACHINE, NXSERVER, FreeNX"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-03-29
Using NXSEVER, I get a Black Screen when I remotely log in to my Ubuntu PC.  I was able to remote in until yesterday.  I have another user account that works as it should.  The NOMACHINE website states that this is a issue with GNOME and to remove Gnome config and tmp files.

I found somewhere to rm -r -f /tmp/* to delete temporary files but that does not work for me.

I found that some said to SSH into the PC and issue ...
  $ DISPLAY=localhost:1004
  $ gnome-session
... but that did not work for me either.

I note that there are a lot of "Black Screen" posts on the web and NOMACHINE states that it is a GNOME problem.

Anyone have any insights?

Thanks

Carl

---

### Post by cwmoser on 2008-04-12
Finally found a solution.  I spent quite a bit of time experimenting and Googling for a solution.  From the number of posts on the Internet, this "black screen" issue has plagueued quite a number of us who use Nomachines NXserver and FreeNX.  

So here is how I got it to work.  I created another user account (carl2) which would work with NXServer.  But, my main login account (carl) still gave me the black screen.  I struggled using my second account as I had everything set up in my original account.  So, this is how I fixed my original account that had the "black screen" problem.

cp  /home/carl2/.Xauthority  /home/carl/.Xauthority
corrected .Xauthority so that it had 600 permissions and owner/group = carl

corrected .dmrc so that it had 600 permissions and owner/group = carl

edited my /home/carl/.profile and commented out all the "export" statements.  I had some for PATH, PKG_CONFIG_PATH, MANPATH, and LD_LIBRARY_PATH.



Hope this helps others.

Carl

---

