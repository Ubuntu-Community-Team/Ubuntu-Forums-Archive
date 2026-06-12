---
title: "Odd problem with middle click in browsers"
date: 2008-03-16
forum: Arch and derivatives
---

### Post by TheOrangePeanut on 2008-03-16
Alright, I'm on my old, old PC that I never use except when I'm at my parents house.  I've got a fairly recent installation of Arch equipped with XFCE on it.  Since this is basically my experimental machine, and Firefox has been kind of slow, I decided to try out some alternate browsers.  Well, I noticed something weird that is strange between all three of the graphical browsers I am using (Firefox, Kazehakase, Opera).

All of the problems stem from the mousewheel.  The first probelm is that if I roll the wheel up very, very quickly, it will make the browser go back, just as if I had pressed the back button several times.  The second problem is also peculiar.  If I middle click in any open area (anything thats not a link, basically) Firefox and Opera will automatically go to [www.easy.com](www.easy.com).  No idea why.  In Kazehakase, if I middle click in a simlar area, it automatically does a google search for "easy".  Strange, right?

It's even more peculiar because it happens in three different browsers.  They are all at their default setting as far as mouse buttons are concerned; I've never had this problem on my other machine which runs Linux Mint.  

Any idea what the problem is?  It doesn't even make sense to me how this could happen.

---

### Post by disturbed1 on 2008-03-16
For Bon Echo and other Mozilla based browsers.

about:config

middlemouse.contentLoadURL

set that to false.

It's the option that will attempt to goto which ever url is loaded in the clipboard. So if you highlighted easy, then press the middle click button, it will attempt to goto [www.easy.com](www.easy.com). If you highlighted (which puts selected text in the clipboard) sfd9a87safd firefox will attempt to goto that website, but since it doesn't exist, it will google search for it.

---

### Post by D-EJ915 on 2008-03-17
for opera, hit CTRL-F12 then click on advanced, then shortcuts, and in-between the 2 white parts on the right it has "middle click options"  I don't know how to disable it completely though, but sometimes I find it useful so I've never looked.

---

### Post by sarah.fauzia on 2009-01-22
I could only get middle-click search in Kazehakase by following this solution and then disabling clipboard.autocopy in about:config. I came here googling for a solution to my problem :).

---

