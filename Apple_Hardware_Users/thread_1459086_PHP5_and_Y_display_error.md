---
title: "PHP5 and Y display error"
date: 2010-04-20
forum: Apple Hardware Users
---

### Post by TehSnarf on 2010-04-20
I finally got around to installing 9.10 server on a mac mini I've had lying around forever. I'm just going to be using it for personal web hosting and a few other random things that interest me... I installed everything just fine. Works like a little champ, actually, although I have come across one minor issue. I installed php5, mysql, apache2, and then WordPress without issues, but now when I view the page, WordPress is spitting out the year as though it's 0000 when using Y, but if you use y, it displays '10' correctly. Found some other articles on the issue, and from what I gather it was corrected in SVN, but that's where I get lost.

I assume I'm going to have to compile PHP5 from source, and I've grabbed the php5.3-201004210230.tar.gz from their webpage, extracted, installed build-essential and a few other dependencies ./configure complained about, but I'm not sure that this is going to produce php with all the fanciness I have already.

Are there other steps I need to go through in order to get this working with mysql and such? Is there somewhere I can file a bug report on this, if I need to? Should I just spike this mac mini and break out an old pc instead?

---

### Post by TehSnarf on 2010-04-21
So I went ahead and upgraded it to 10.04 using "sudo do-release-upgrade -d", let it update everything, rebooted, and poof. Problem solved. You guys sure are helpful!

---

