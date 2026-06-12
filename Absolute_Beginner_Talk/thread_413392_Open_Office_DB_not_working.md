---
title: "Open Office DB not working"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-04-19
Ok, I still consider myself new to Ubuntu - about a month into it now.
Tried to set up a relational database in Open Office - it would be a copy of one I have used since version 1.0 of MS Access.

The initial version of this database would not be considered complex.  I need two tables - one with a Key, the other with a "foreign" key.

I used the wizard to setup both tables, no problem.  Used the forum wizard to set up form and subform, used drop down boxes to indicate usage of the relationship.

Eventually, I get to the point where I need to click finish to use or modify the form.  At this point, nothing happens.  I can click finish until the cows come home, still nothing.  Is this app broken on my machine, or am i doing something wrong?

Thanks.

Caruso

---

### Post by jandrews82 on 2007-05-09
Don't worry mate, it's not just you or your machine.  There are hundreds of posts all round the internet about this problem and most people suggest changing your Java settings under OO to get it sorted although this still sometimes seems like a bit of a sketchy answer.

Try playing with your Java settings anyway.  That's what i'm doing and i'm struggling with the latest release of Kubuntu.

Best of luck.

---

### Post by carusoswi on 2007-05-10
So, I guess I am surprised that such a basic function in such a critical ap is buggy in Ubuntu.  I had this problem in version 6.10 so it is not new or unique to 7.04.  Thanks for the heads up, though.

Caruso

---

### Post by swisscow on 2007-05-11
I've had this as well. Solved it by removing everything I could find on open office in Synaptic, downloading from the open office web site the install rpm, converting it to Debs and installing. I followed some instructions somewhere on this forum (can't find it now!) but essentially what I did was:

Cleaned out open office through Synaptic
Installed alien through synaptic
Download the tarball from the open office web site to the desktop and extracted it
Renamed the extracted folder to something easier, like office
Then in terminal:

```
cd Desktop
cd office (or whatever you called the extracted folder)
cd RPMS
sudo alien --scripts --keep-version *.rpm
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *.deb
```

Worked fine for me and solved the database problem
As I said this isn't my solution so if you try it and have any problems I probably can't be much help.

Good luck

---

### Post by carusoswi on 2007-05-11
Thanks for the tip, SwissCow.  Will give that a try when I get back to my Ubuntu box this evening.
Caruso

---

### Post by swisscow on 2007-05-13
No problem, hope it works

Actually did it again myself today with Kubuntu and worked sweet.

Good luck!

---

### Post by steve.horsley on 2007-05-13
Another reason for replacing the mangled openoffice that Ubuntu ships with is that if you change your theme at all, then all the icons in OpenOffice disappear, to be replaced with text. This doesn't happen with the real OpenOffice.org downloaded from their site.

---

### Post by Hagar Delest on 2007-09-15
> **steve.horsley said:**
> Another reason for replacing the mangled openoffice that Ubuntu ships with is that if you change your theme at all, then all the icons in OpenOffice disappear, to be replaced with text. This doesn't happen with the real OpenOffice.org downloaded from their site.
Because the Ubuntu team has split the install files into multiple packages. The icons sets are in the packages openoffice.org2-style... in Synaptic. But it's a rather bad idea, I agree.

---

