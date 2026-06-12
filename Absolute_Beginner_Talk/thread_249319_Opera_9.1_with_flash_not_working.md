---
title: "Opera 9.1 with flash not working"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-09-02
I, like many others, seem not to be able to get Flash to work on their system with Opera, (mine is Ubuntu linux). What I have noticed is that when I go to a page on my website which has animated (moving) text but which is not displayed, even with the 'enable Java' button ticked and then leave that page,when I go back to that page and check Tools/Advanced/content the 'enable Java' box is unticked. Any solutions to this would be appreciated. BTW has anyone who uses Opera had any luck getting flash to download and work in Ubuntu.
regards

---

### Post by ThrobbingBrain66 on 2006-09-02
are you having problems with java or flash...or both maybe?  i have had both working for some time now.  I just pointed opera to my firefox plugin folder to get flash to work. the other mplayer plugins (current firefox plugins didnt work for me) i downloaded from this page:

[http://my.opera.com/community/forums/topic.dml?id=131761&t=1151357109&page=1#comment1512034](http://my.opera.com/community/forums/topic.dml?id=131761&t=1151357109&page=1#comment1512034)

and for java, you have to set the default java path (tools>preferences>advanced>content>java options).

/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386 is the path you want

---

### Post by Sbarton on 2006-09-07
Sorry about delay in replying. After uninstalling /reinstalling, and thro' terminal typing (sudo aptitude update
sudo aptitude install sun-java5-bin) without brackets.Checking that the file path was correct, ensuring that java was enabled (in Opera)it finally worked.
Many thanks for your input.
Regards

---

### Post by pak33m on 2006-09-07
I live and breathe out of Opera.  I couldn't imagine myelf going back to any other browser.  Enough of the testimonial...

If you haven't installed Flash already, then you will need to do so.  

Go here: [http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

During the install you will be prompted to install the plugins for your Opera install.  You will need to install to /usr/lib/opera/plugins (if applicable).

At least this is what I've done.  I hope it works out for you.

---

### Post by mcpish on 2006-09-14
I don't know what the deal is but I can never download that file from the Adobe site, I have no clue how others are doing it.  I click on that file and it never downloads, it just times out.  No matter what browser I use. Other downloads work fine, just that specific file I've never been able to get from Adobe, I've been trying for **months**.

Here's a screenshot, it just sits at this point forever, but never finishes, even though I download tons of other stuff from other sites.  I have a 10 mbit/sec internet connection.
[IMG]http://mcpish.no-ip.info/stalled.png[/IMG]

---

### Post by pak33m on 2006-09-14
mcpish,

Check your PMs.  

Once you get the file follow the directions here from my original post.  You're going to be prompted to install te plug-ins for Mozilla-Firefox, but make sure that you install again for Opera.

Hope this all works out for you.  I don't know where I'd be with Opera.  And Ubuntu of course!

---

