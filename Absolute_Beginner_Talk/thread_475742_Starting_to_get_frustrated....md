---
title: "Starting to get frustrated..."
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Mallette on 2007-06-16
I have the thread "How do I know it's working..." but haven't had a response today.  I've made a bit of progress.  I can see my wireless network, but there is no WPA option so I cannot connect.  Trolling through the posts I found instructions to create a wpa_supplicant.conf file and put it in the "etc" directory.  What's frustrating is the I a told (this is SO Windows like!!!) I am not the owner the owner and don't have permission.  First of all I HATE these kinds of defaults in Windows and am sorry to find them here.  If I want to burn my laptop it's my business, not a coder...

Anyway, I cannot find a way to log in as owner (though I SHOULD have been registered as such by virtue of having done the install).

Dave

---

### Post by sloggerkhan on 2007-06-16
Well.... you can always type su from the command line, though on ubuntu sudo is preffered. You also probably have a root account.

---

### Post by HotShotDJ on 2007-06-16
Did you look at the excellent [documentation]("https://help.ubuntu.com") already available to you? [Here]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") is the section specific to WPA. It would probably be a very good idea for you to go through [this]("https://help.ubuntu.com/7.04/newtoubuntu/C/index.html") entire section, however [this]("https://help.ubuntu.com/7.04/administrative/C/") part specifically addresses your issues with permissions.

Once you get used to it, Ubuntu is actually easier than dealing with Windows.  But it can sometimes be frustrating during the initial learning phase.

---

### Post by Mallette on 2007-06-16
Thanks.

I checked some other posts and found something called "Nautilus" that appears to be otherwise unreferenced.  I was able to change permissions.  However, this was not intuitive.  I still don't know what "Nautilus" is.  I don't even know what su or sudo represent.  

I am hardly new to computing and go back to punch cards.  I am determined to learn this but would like to locate a definitive reference.  Are there any?

Dave

---

### Post by Dr Small on 2007-06-16
"Nautilus" is your file browser.
Example, if you click on "Places", and then "Home Folder", it opens Nautilus and browses to /home/$user folder.

Sudo is used to run as "Super User", or "Root".
If you run a command that says you don't have permission to run that command, place "sudo" in front of the command, and it will ask you for your password. Enter your password, and you are now running the command as root.


Dr Small

---

### Post by kevdog on 2007-06-16
Other than a lot of complaining, I really cant figure out the point of your post.  Id be more than willing to help you, however, by reading this post I really cant deduce exactly what your problem is.  Obviously it has something to do with WPA, but Im not exactly sure of the details.  Look if you want people to help you, you need to be specific not only about your problem, but help us out by telling us about your hardware, and what you have tried very specifically up to this point.

Take a look at this link:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Maybe that will help you.  
Have a great day, but QUIT ALL OF THE COMPLAINING!

---

### Post by Mallette on 2007-06-16
kevdog:
You are correct, sir and I apologize.

It's just been a long morning...

I'll get there and I appreciate both the help as well as all the effort that has gone to make this possible.

Kind regards to all,
Dave

---

### Post by dwhitney67 on 2007-06-16
You may not be new to computing, but it appears that you are new to Linux/Unix.  That is OK.  May I suggest that you procure a book concerning Linux System Administration.  You do not have to become an expert, but it would be helpful if you knew the basics, especially in the areas of file permissions.

Windows has mildly embraces the concept of protecting files from non-privileged users, however it seems that most people run Windows from an account that has administrator privileges.  Hence the reason why there are so many computers vulnerable to viruses.

Linux, and in your case, Ubuntu, is more protected than Windows will ever be.  It clamps down on a non-privileged user's ability to modify system files.  Of course, at any time you can modify these protected files by first becoming a sudoer (pronounced su-do-er) or the superuser.  For the former, you precede commands with the 'sudo' statement and for the latter, you log as the superuser using 'su'.

For example, to edit /etc/hosts (with write permissions) you would need to enter a 'sudo' command such as:

[FONT="Courier New"]sudo gedit  /etc/hosts[/FONT]

Likewise you could do this:

[FONT="Courier New"]su
<type root password>
gedit /etc/hosts
<logoff when done>[/FONT]

When I first set up my Ubuntu system, I cannot recall setting up my root password.  I only recall setting the password for my user account.  I dug into the issue and found that I can set my root password by going to **System -> Administration -> User and Groups** (and then entering my user password, so that I could become a sudoer).  Afterwards I edited the properties of the root account to include the password of my choice (and not the Ubuntu default!).

Anyhow, I hope my post enlightens you a bit to the Linux world.

---

### Post by Mallette on 2007-06-16
Yezzir, I've a long way to go.  Nearest to Unix/Linux I've been is the old lamented Amiga OS back in the nineties.  

I am going to peruse the docs I was directed to.  

After getting permissions set and dropping the wpa_supplicant.conf file in the etc folder, I now cannot get any properties or response from the Network at all either through the top icon or the "System" command.

one forward, 2 back...

ONWARD! Through the fog...

Regards,
Dave

---

