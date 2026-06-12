---
title: "Bug Buddy is not my buddy"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by Bloch on 2006-06-05
Totem crashes when I change certain preferences. I have a clean install of Drake.

So I chose "Inform Developers" on the pop up menu, and Bug Buddy came up.  I spent about 40 minutes checking that the bug was not reported, filling in the description, testing to see if the bug always works the same way. 

After all that work I came to a page that askes me where "sendmail" is. "Please check the path to sendmail" it asks me.

So I looked up ubuntu help on Bug Buddy. I read through 8 pages. All well written and helpful.
On the 9th page it says:
Bug Buddy gives you two options.  You can either send the report
  directly to the bugs database using sendmail,
  or you can save the report to a file and submit it manually.
Bug Buddy uses sendmail to send
      email to the bug tracking system to submit the report.  This field
      specifies the exact location of the sendmail command
      on your system.  Bug Buddy fills in this field automatically if it
      detects sendmail on your computer.  Usually, you will
      not need to change this setting.

I know nothing about sendmail, so I try to look further into the possibilities of submitting the report manually.

There is no information about this.

How can I report this poor documentation to the Bug Buddy developers? What is the point in them creating a user-friendly reporting system, in simple language, with pages of help, and then this one block mentioned in passing. 

Poor documentation makes this program unusable - isn't that also a bug?

---

### Post by fluffington on 2006-06-06
AFAIK, Ubuntu uses [exim]("http://www.exim.org/") and not sendmail. I don't know anything about MTAs, so I don't know if Bug Buddy can use exim in place of sendmail, but if you want to install sendmail, you have to enable the universe repository and do:

```
sudo apt-get install sendmail
``` 
As for complaining about Bug Buddy's documentation, you can use the [GNOME bug tracking system]("http://bugzilla.gnome.org/"). The author's e-mail address is also listed on the [freshmeat.net project page]("http://freshmeat.net/projects/bug-buddy/").

You may also want to [file a bug for Ubuntu](https://launchpad.net/distros/ubuntu/+bugs) (assuming there isn't one for this already), as it's nonsensical for something in main (Bug Buddy) to require something in universe (sendmail) for basic functionality.

---

### Post by u.b.u.n.t.u on 2006-06-06
"How can I report this poor documentation to the Bug Buddy developers?"

I hear you loud and clear on that! lol Hopefully reporting bugs can be made easier as I would like to contribute in this manner.

---

### Post by Bloch on 2006-06-06
As Fluffington advises, you have to install sendmail first in order for Bug Buddy to work.

I searched Launchpad on the link he provides and found that it has indeed been reported as bug 36780 (the bug reporter misspells sendmail as senmail in the title)

[https://launchpad.net/distros/ubuntu/+source/bug-buddy/+bug/36780](https://launchpad.net/distros/ubuntu/+source/bug-buddy/+bug/36780)

Here's what it says:
> At the end of the bug report bug-buddy gives me a choice to send the report with sendmail or to store a file to send it later, but as I didn't install sendmail (I think it is not installed by default because I don't remember to have unselected it, and it is not a dependency for bug-buddy) I could not send the report from bug-buddy.


However the documentation still needs improvement. It asks if you want to submit a bug report manually. If you click Yes it will create a nice text file report. But there is no information on how to submit it manually and no mention of where to get that information.

I'll take a look around and see who I can contact . . . it seems important to me that bug reporting should be made user-friendly.

---

### Post by fluffington on 2006-06-06
After doing some further reading, I think that Exim should work fine with Bug Buddy. Exim is in main, but it's still not installed by default. You'd have to do one of the following to install it:

```
sudo apt-get install exim4-daemon-light
```

or

```
sudo apt-get install exim4-daemon-heavy
```

I installed it on my computer, but haven't yet had the opportunity to test its compatibility with Bug Buddy.

---

### Post by fluffington on 2006-06-06
I just tested it and Bug Buddy does, in fact, work with Exim. Just install exim4-daemon-light and tell Bug Buddy that sendmail is at /usr/sbin/sendmail (that last part might not be necessary, but that's where the exim package puts the sendmail symlink).

---

### Post by H.E. Pennypacker on 2006-06-25
I had no problems with Bug Buddy using sendmail.  All you have to do is download "sendmail" from Synaptic, and at the last step of Bug Buddy, put in /usr/sbin/sendmail.  Do it exactly as I typed it: /usr/sbin/sendmail. 

It sends the report to [email]submit@bugs.gnome.org[/email].

---

### Post by insanitywetrust on 2007-01-29
same here

i did a reboot after upgrading a Lot of software or something and now i cannot get desktop to load correctly, and too much music to just throw it all away and start over

so, what can i do to at least turn that software off, or better yet, can i uninstall this bug buddy? and also, how can i get back to the normal desktop,

---

### Post by Mark_in_Hollywood on 2007-04-16
[email]submit@bugs.gnome.org[/email]

---

