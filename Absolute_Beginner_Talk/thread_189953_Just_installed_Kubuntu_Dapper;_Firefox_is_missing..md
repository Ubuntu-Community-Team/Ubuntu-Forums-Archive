---
title: "Just installed Kubuntu Dapper; Firefox is missing."
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by drowned_in_milk on 2006-06-05
I just did an install of Kubuntu 6.06, and everything seemed to go smoothly, but I cannot find Firefox anywhere.  It is not in Applications > Internet, and the only package I can find in Adept is "mozilla-firefox-locale-en-gb".  I've also updated Adept via "Fetch Updates" numerous times, and that is still the only Mozilla package that shows up.

What did I do wrong?  How can I install the Firefox package?

Thanks

---

### Post by catlett on 2006-06-05
try apt-get from the terminal
```
sudo apt-get update
``````
sudo apt-get install mozilla-firefox
```

P.S. if that doesn't work post your repository list, use this command if you don't know and cut/paste it to a reply > sudo kwrite /etc/apt/sources.list

---

### Post by drowned_in_milk on 2006-06-05
Thanks.  However, I just get this:

```
Reading package lists... Done
Building dependency tree... Done
Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-firefox has no installation candidate

```

My repository list is:


# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by drowned_in_milk on 2006-06-05
Would this be caused by a botched installation attempt?  Everything else seems to work fine.

---

### Post by catlett on 2006-06-05
No. I think you are going to be fine in a minute. You don't have any repositories open. I'll explain after. Right now do this.
DELETE all the "#"s in front of the lines that start with "deb". Open the list again the same way and remove the # mark in front of the lines with deb.
Quickly a # tells the computer to ignore what follows. What follows in your case are the repositories. You have them all ignored. The repositories are where the applications come from.
After you remove the #, do this ```
sudo aptitude update
``````
sudo aptitude dist-upgrade
```

P.S. firefox should install with the dist-upgrade but if it doesn't, repeat the earlier commands.

---

### Post by catlett on 2006-06-05
Now to explain a little bit. A "#" means one of two things. It is either identifying the next line as a comment and therefore should not be looked at as text to execute. Or it is a symbol of ignore. It symbolises "what comes next is to be ignored".
In your case every repository is labeled an explanation or comment. So a # is put in front of the comment about the repository and then the repository is not commented.
Somehow your installation had an error. > # Line commented out by installer because it failed to verify:For some reason the installer could not verify the repository server. So it commented the lins out. You ended up with no repositories.
Now you have opened them up. Actually I just thought of something. Do you have an internet connection? Or did you install from a cd without an internet connection? This isn't going to work if you don't have an internet connection.
If you have an internet connection, the rep[ositories will be open to you and firefox will install along with whatever else you want from the ubuntu repositories.

---

### Post by drowned_in_milk on 2006-06-05
Yes--I was able to connect to the internet before I installed.  The only thing I can think of is possibly when it told me installation was done and that it needed to reboot, it froze up, and after a few minutes of nothing responding i killed the power and then restarted it again (everything booted up smoothly though).

Anyway, everything is working now.  Thank you ever so much :-)

---

### Post by catlett on 2006-06-05
Great! Glad it was a simple fix. It appears the install went fine other than the reboot and maybe something during first boot sets up repos? I don't know but you'll be fine now. 
Your welcome and like the catch phrase goes, "don't pay me back, pay it forward":)

---

