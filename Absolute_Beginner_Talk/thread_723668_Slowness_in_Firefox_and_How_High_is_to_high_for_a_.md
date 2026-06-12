---
title: "Slowness in Firefox and How High is to high for a load average?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Xplunger on 2008-03-13
Was wondering about those two. For some reason my firefox seems a bit slower than when I was running xp, like when I am scrolling down a site with a lot of media, it seems sluggish.

---

### Post by chewearn on 2008-03-14
Have you enable the restricted video driver?  The Restricted Driver Manager will pop-up to prompt you about it after installation.

---

### Post by Slipmyknot101 on 2008-03-14
Hi,

I've had Firefox performance problems as well, and I've partially overcome these problems by taking the following steps:

1. Open a blank tab in Firefox and type > about:config2. If you have never been here before, a huge list of Preference Names and Values is going to show up. Focus on the search bar that is somewhere below the address bar, and is labeled, "*Filter*".
3. In this "*Filter*" bar, type the following: > network.http. and the huge list of Preference Names and Values will be filtered down to roughly 19-21 values.
4. First, focus in on the filtered result that is entitled: > network.http.max-connections and assuming that you have never done this before, the Value, when you follow the Preference Name horizontally to the applicable value is going to be set at 24 connections as the maximum. Click and highlight the the Preference Name that is entitled > network.http.max-connections and the entire horizontal region should highlight in blue. Move the cursor over to the value, (24 if you have never before modified the setting), and double click on it. A window will pop up. You will now have the opportunity to change that 24 to another value. Please change the 24 to > 48. Press OK and the small window will close.
5. Second, focus in on the filtered result that is entitled:> network.http.max-connections-per-sever. The default value for this Preference Name is set at 8 connections per server. Change this value to > 12.
6. Third, focus in on the filtered result that is entitled: > network.http.max-persistent-connections-per-server. The default value for this Preference Name will be 2 persistent connections per server. Change this value to > 6.
7. Fourth, focus in on the filtered result that is entitled > network.http.pipelining. The default value for this Preference Name is false. Change this value to > true.
8. Fifth, focus in on the filtered result that is entitled: > network.http.pipelining.maxrequests. The default value for this Preference Name is 4 requests at the maximum. Change this value to > 8.
9. Sixth, focus in on the filtered result that is entitled: > network.http.proxy.pipelining. The default value for this Preference Name is false. Change this value to > true.
10. Seventh, focus in on the filtered result that is entitled: > network.http.request.max-start-delay. The default value for this Preference Name is 10 seconds. Change this value to, but only type the number, not the text, "(zero)", as the "(zero)" is only meant to indicate that "0" is really "zero" and not "O" (oh). > 0 (zero).

After you have changed the above settings, restart Firefox. This is done when all of the windows that are affiliated with Firefox have been closed. Open Firefox again, and check to see if you have gained any performance. If not, that is Ok. There are other options.

The second recommendation is that you check out some of the other browsers that are supported (not necessarily officially) by the Linux OS. Examples of these browsers are:[LIST]
[*][Epiphany Web Browser]("http://www.gnome.org/projects/epiphany/")
[*][Galeon Web Browser]("http://galeon.sourceforge.net/")
[*][Amaya Web Browser]("http://www.w3.org/Amaya/")
[*][Dillo Web Browser]("http://www.dillo.org/")
[*][Links Web Browser]("http://links.sourceforge.net/")
[*][Opera Web Browser]("http://www.opera.com/download/index.dml?platform=linux")[/LIST]If none of these are satisfactory, or if they do not suit your needs, you may also want to try [Firefox 3.0 BETA]("http://www.mozilla.com/en-US/firefox/all-beta.html"). From what I have heard, though I have not spent extensive time with Firefox 3.0 BETA, many aggravating compatibility and connectivity issues are addressed and for the most part, solved, at the temporary expense of not having as much add-on compatibility due to the lack of usage in the mainstream Firefox community.

If you have any other questions, please feel free to ask.
I hope this helps.

Sincerely,
Trevor

---

### Post by Xplunger on 2008-03-14
Thanks for the post I read through it, I'm going to attempt that later, when I'm more awake and less likely... to mess it up.

---

### Post by Trzone on 2008-03-15
I followed every step and it seems to have increased page loading time, and has stopped the freezing up for me.  thanks! :)

---

