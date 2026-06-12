---
title: "Customize the color of openoffice.org menus?"
date: 2006-08-18
forum: Art &amp; Design
---

### Post by MikeMLP on 2006-08-18
Let me preface this by saying that I posted a similar message on the openoffice.org forums and did not get any response.  With that said, on to the message:

I am using a wonderful dark theme on Gnome. While most applications can be themed so that their menus appear white, rather than black, Openoffice.org and Firefox are two that cannot be themed through Gnome and must have their visual settings changed from within. I altered Firefox using the userChrome.css file: [http://www.mozilla.org/support/firefox/edit](http://www.mozilla.org/support/firefox/edit) and I am wondering if there is a similar way (using a GUI within Openoffice or a configuration file) to change the color of menu title text from black to white. Attached is a screenshot of what I currently have, so you can see what I am talking about:

[http://img205.imageshack.us/my.php?image=screenshot2zd2.jpg](http://img205.imageshack.us/my.php?image=screenshot2zd2.jpg)

I'm sure you dark-theme lovers out there have run into, and solved issues like this, so if you have, please speak up!  Thanks!

P.S.  I am very sorry that imageshack is slow, and sometimes doesn't respond... I know the pic is there...  I may change hosts in a bit... hang on...

---

### Post by distroman on 2006-08-18
Any chance you could let me in on how, you fixed firefox. I saw your links, but I need a bit more help.
What exactly needs to be added to the userChrome.css file?
Thanks

ps
I am curious about openoffice as well, as you can imagine, though it's not as bad as firefox.

---

### Post by distroman on 2006-08-18
I think I am getting close. Got the menu to highlight with white.
However the text stays black, if I don't move the mouse over it. 
Could someone tell me how to fix it, so the text stays white?

```
/* Make menus XP style */
menupopup, popup {
   border: 1px solid ThreeDShadow !important;
   -moz-border-left-colors: ThreeDShadow !important;
   -moz-border-top-colors: ThreeDShadow !important;
   -moz-border-right-colors: ThreeDShadow !important;
   -moz-border-bottom-colors: ThreeDShadow !important;
   padding: 2px !important;
   background-color: white !important;
}
menubar > menu {
   border: 1px solid transparent !important;
   padding: 2px 5px 2px 7px !important;
   margin: 0 !important;
}
menubar > menu[_moz-menuactive="true"] {
   background-color : white !important;
   color: white !important;
}
```

Thanks

---

### Post by MikeMLP on 2006-08-18
The firefox menu question was actually answered in the comments section of an early version of the Linsta theme (which I am currently using):  Just do a copy paste and you're done

[http://www.gnome-look.org/content/show.php?content=42697&forummode=2&forumpage=2&forumexplevel=all](http://www.gnome-look.org/content/show.php?content=42697&forummode=2&forumpage=2&forumexplevel=all)

and for posterity's sake (and as a backup in the unlikely case gnome-look suddenly goes POOF, here is what you add to the .css file.  
```
menubar > menu {
color: white !important;
}

menubar > menu[_moz-menuactive="true"] {
color: white !important;
}

menubar > menu[_moz-menuactive="true"][open="true"] {
color: black !important;
} 
```



Note, I had to go searching for the correct file, as there were several firefox "profile" folders on my system for some reason.  I had to search until I found the right one, which, I believe, was at /etc/firefox/profile/chrome

now I can't believe that none of you über Linux users that haven't had a windows box for the past 9 years have never been able to customize the openoffice menus to work with a dark theme before... I know someone out there knows the answer, and I *dare* you to post!

:mrgreen:

---

### Post by distroman on 2006-08-19
Thanks, that did it.
I am using this one [http://www.gnome-look.org/content/show.php?content=43054](http://www.gnome-look.org/content/show.php?content=43054)

Hope just like you, someone knows how to solve openoffice.

---

### Post by bvc on 2006-08-19
well does oo use user custom files? If yes, it's probably in there somewhere very similar to firefox, if no, then no. i don't have oo so I can't check

---

### Post by Francewhoa on 2012-02-19
I posted a solution at [http://ubuntuforums.org/showthread.php?p=11702323#post11702323](http://ubuntuforums.org/showthread.php?p=11702323#post11702323)

---

### Post by overdrank on 2012-02-19
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

