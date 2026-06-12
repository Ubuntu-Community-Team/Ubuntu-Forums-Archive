---
title: "Adding External Program to Bluefish?"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by andrew.46 on 2006-12-26
Hi,

 I have been using Bluefish 1.0.4 to design my father's site:

[http://www.strong-family.org](http://www.strong-family.org)

 on Xubuntu 6.06. Only problem that I have been wrestling with is the correct syntax and command to add an external viewer: Firefox. (Under: Edit / Preferences / External Programs )

 I believe that the path to Firefox is as follows:

/usr/lib/firefox/firefox

The command immediately after the path should (I think) be:

%s&

making the whole line

/usr/lib/firefox/firefox %s&

 But this does not work!!! Can any Bluefish / Xubuntu users give me a steer on this slightly exasperating problem?

          Thanks for your help!!

                    Andrew

---

### Post by jive_turkey on 2006-12-26
Don't hold me to this but the path to Firefox is:

/bin/mozilla-firefox
or
/bin/firefox

That is if you are trying to launch Firefox from Bluefish

---

### Post by ariel on 2006-12-27
I'm using bluefish/firefox too; the config working for me is:

/usr/bin/firefox %s&

(you can always find the proper path for any app in the path doing for example:
which firefox
)


Now what i'd like to know is how to make bluefish launch firefox with the "view in browser" icon...

---

### Post by ariel on 2006-12-27
Reply to myself :): just replace the first entry in the External program list (the useless galeon entry) with the Firefox entry as mentioned above.
:)

---

### Post by andrew.46 on 2007-01-21
Hi ariel,

 Thanks for your advice:

> **ariel said:**
> I'm using bluefish/firefox too; the config working for me is:

/usr/bin/firefox %s&

(you can always find the proper path for any app in the path doing for example:
which firefox
)
.


 Your setup appears exactly the same as mine: which firefox reveals "/usr/bin/firefox" so I added the same command to the Bluefish preferences but still no browser will open to preview the files!!

 Any ideas? I am running Bluefish 1.0.5 and Firefox 1.5.0.9 and apart from this exasperating problem I absolutely love the program :-)

                         Andrew

---

### Post by andrew.46 on 2007-01-21
Hi,

 I have found a soltion to this problem which I am posting here for the benefit of others. I posted a ticket at Launchpad:

[https://answers.launchpad.net/bluefish/+ticket/3279](https://answers.launchpad.net/bluefish/+ticket/3279)

 and received the following answer from a gentleman named Curtis which resolved the problem completely:

> Consider either of these commands:
firefox -new-window "%s" &
firefox -new-tab "%s" &

Firefox 1.5 and above switched the remote command line and you may need to explicitly declare your intention. I placed the file/URL in quotes in the above example to hide some characters from being interpreted by the shell at startup.

 The first example worked for me, I did not test the second.

                Regards,

                    Andrew

---

