---
title: "Installing files/ packages needed to run penggy?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by New_to_this on 2007-10-24
:confused::confused::confused:Does any one know how to install and configure the packages to run penggy? I don't have access to my info right now (at the library) but I believe they are titled Debconf , guile 1.6? and glib . They were downloaded off the debian site where I downloaded penggy. I have been playing around with the thing for hours at a time and still no wheres near the end- I can't get penggy up and running- hence I can't get on the internet with that computer. Can someone please help?  No one answered my earlier post and I have searched the internet trying to figure out how to no avail. IS ANYONE OUT THERE???? Thanks in advance.

---

### Post by jfinkels on 2007-10-24
Read the first link in my signature about "Installing software". You should always be installing software using either 'apt-get' or Synaptic, the graphical package manager.

To install the package 'penggy', type the following in the terminal ("Applications > Accessories > Terminal"):```
sudo aptitude install penggy
```
Type your password when prompted.

---

### Post by New_to_this on 2007-10-31
Hello. Thank you for the reply. I think I have figured out how to install the dependencies. Now I  have another problem. I can't get penggy to activate- it keeps telling me I have a bad configuration. It states that it can't find phonetab and aol-secrets. However, they are both there and I have edited everything according to the info posted on the web. Any advice? Thanks.

---

### Post by jfinkels on 2007-11-01
Did you install using:```
sudo aptitude install penggy
```? I HIGHLY recommend installing it this way, if you didn't.

I'm afraid I am unfamiliar with the software 'penggy', so I don't really know how it works, but if you post any error output here, perhaps someone else with more experience will be able to help you.

Have you tried running the program in the terminal? You may get more descriptive error messages.

---

### Post by New_to_this on 2007-11-01
Hello. Thanks- I finally got penggy running but can't get fire fox to go anywhere- I'll start another post on that issue. Thanks again

---

