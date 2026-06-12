---
title: "lost my root?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by YeahBuntu on 2006-09-08
Ok .. Im sorry to bother you all again ..I am following the instructions [here]("http://howtoforge.org/lamp_installation_ubuntu6.06")  and I am to the point where I am supposed to log into webmin and configure.  It says to log in as root so.. I put root in the username field and I put in my password that I used o install and this does not seem to work.  So I put in my username that I use to loginto gnome and my password and it keeps telling me my login failed.  Hope someone can help here.. did I forget a password or a login name I should have ..remembered?

Ok this does not look good I just got a message saying that the host has been blocked for too many authentication failures.... oh lord I knew i was gonna mess somehing up :oops:

---

### Post by jordanmthomas on 2006-09-08
to make a root password, type this in a terminal (as your normal user)
```
sudo passwd root
```

To be able to log into Gnome as root, go to System --> Administration --> Login Window
Then go to the Security tab where there will be something along the lines of "Allow local Administrator to lo login"  and check it.

I assume you understand the perils of being root?

---

### Post by jordanmthomas on 2006-09-08
As for being blocked, I believe you can just wait a little while and try again.  If not, a reboot will certainly fix it.

---

### Post by aysiu on 2006-09-08
You don't need to set up a root login, just do ```
sudo -s
```

---

### Post by YeahBuntu on 2006-09-08
this does not seem to be working... I do login using the name I see next to root@xxxxx   where xxxxxx is the username I should use to log into this with right?  I realize I may be asking for too much here .. I did run the sudo -s command in the terminal and it asked me for my pw which I provided and it took it just fine... but I still cannot seem to get logged into webmin.

---

### Post by YeahBuntu on 2006-09-08
Ok so I am trying to run the changepass.pl as described in the faq for webmin.  Problem is every time I /usr/libexec/webmin/changepass.pl /usr/libexec/webmin admin foobar as described in the script..

bash keeps saying changepass.pl command not found.... 

How much of a total doofus am I.

---

### Post by YeahBuntu on 2006-09-08
I am a true Linux Newb as many of us are.  If anyone has the same problem I did this is for the search function:  webmin/login password/unable/changepass.pl

Ok I am getting the hang of this slowly. (dreams) Wish someone around me could hold my hand a bit more because I really hate to mess things up.

Problem:  After installing webmin while using [this guide]("http://howtoforge.org/lamp_installation_ubuntu6.06?from=0&comments_per_page=10")

I was unable to login to webmin.

It kept failing and then saying I was blocked and restricted or something to that effect.  Thankfully after a few minutes however I was able to try more login attempts only to fail time after time.

Me being a true Linux newbie I decided to browse the file system and locate the changepassword.pl script that for some reason never prompted me for the information during install.  I could see the file I wanted to execute and change the password but runing the script simply opened a terminal which was then soundly closed almost immediately after runing it.  I could open the script and read it and see the command argument I wanted to run but I simply could not get it to run.

As a side note I purchased the linux bible by Christopher Negus and for some reason it stuck in my head that I needed to type in su to get to the 'super user' or root user to run the script.

Ubuntu uses sudo to get to the root account.  But I could not figure out why su would still prompt me for a password but then nicely say sorry we could not authenticate you... was very strange to me.

Ok so-- I am familiar with DOS (which is probably a bad thing while trying to get the hang of linux)  So trying to navigate to the webmin folder which was nicely placed in: ```
/usr/libexec/webmin
```   subdirectory.. I tried to navigate to it by typing:

 /usr <and then pressing Enter>

and then typing /libexec <and pressed enter> 

This promptly provided me with this response:
bash: cd/libexec: No such file or directory

My first thought was BS .. WTF theres no such file or directory I can see it when I browse the drive!

The reason libexec is not found is because it is looking for the subdirectory right off the (root) directory instead of under /usr where I am currently at.

So I have to type the whole thing on one line to get to the directory I want

cd /usr/libexec/webmin

I thought I was home free .... NOPE!  How do I execute the changepass.pl file in the terminal window?  I kept trying things like run changepass.pl just to see if it would give me a response saying that it attempted to run

Not a chance.

to run this script you first have to be root.

```
sudo su
```

Then you have to type:

```
./changepass.pl /etc/webmin root mynewpassword
```

gawd who woulda thunk ./ executes a file?? (at least a script file)  well... I didn't.

It is important to know that when you log into webmin using your browser interface that the username you will use is "root" (without quotes) that is what they call admin and with the password you have given it by runing the changepass.pl script.

You do not login with your computername or admin or anything but root.

It is also important to know that this changing of your password **DOES NOT**change your actual root password for loging into SUDO SU it is** only**for webmin.

I hope that my boneheadedness becomes someone elses answered prayer.  Any questions feel free to ask but I assure you I am still a newb.  So if theres a better way or a different way...feel free to post away!

---

