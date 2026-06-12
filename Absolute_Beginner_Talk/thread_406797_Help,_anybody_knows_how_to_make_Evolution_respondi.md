---
title: "Help, anybody knows how to make Evolution responding to clicking http links in mail?"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by tommie74 on 2007-04-11
I receive quite a lot of emails with links to websites in them. I prefer not to have to copy and paste the adresses in firefox everytime... In the evolution status bar it says: Click to open: http:\\....etc. when I move my mouse over a link. But when I do click the link, or double or even triple click it, nothing happens.  Firefox is set as my favorite browser. I am using Xubuntu. Anybody knows if this is supposed to work? Anybody knows how to make this function?
Thx for reading,
Thomas de Graaff.

---

### Post by crispy_420 on 2007-04-14
Are you recieving as HTML or simple text? If text, you won't be able to click on the link and your stuck with copy/paste. This will also assume the sender is sending HTML mail too.

---

### Post by tommie74 on 2007-04-14
It doesn't make a difference wether the source of the mail is html or simple text, in either case clicking a link doesn't have any effect. For example the mail coming from ubuntu forum telling me you responded to my thread has a link to this thread. If I click it nothing happens. The source of this mail is in simple text. If I receive a mail from ebay, it definitely has html code in its source. But the links in such a html mail don't work either. 
Anyhow,
thx for looking, 
and if you have any ideas,
I'm happy to hear them,
Thomas.

---

### Post by freebird54 on 2007-04-14
SIlly question, probably, but is Firefox set as the DEFAULT browser?  In FIrefox, Edit->Preferences->Main <Check now> ...

Just in case... BTW - works fine here...

---

### Post by tommie74 on 2007-04-14
Hello Freebird,
not a silly question at all. I've pushed the button you told me "Check now" but nothing happens then. I've also checked the option to always check if Firefox is the default browser on startup. Makes no difference. When I click a link in my newsreader (Pan) instantly an extra tab opens in firefox opening the link I clicked. So it is supposed to function, the link clicking fascillity in Evolution?
Thx for the help,
Thomas.

---

### Post by freebird54 on 2007-04-14
Certainly does for me - that's how I got here.  I can't find any other options that would stop it functioning either.  Do they (links) show up coloured in Evo for you?

---

### Post by tommie74 on 2007-04-14
Yes they do, blue if not clicked, then after clicking they become red. When I hove over a link the status bar shows: "click to open  [http://ubuntuforums.org/](http://ubuntuforums.org/).... etc. "  Maybe evolution is not looking in the right place to find the default webbrowser on my system (Xubuntu).. 
Thx again for helping,
Thomas.

---

### Post by tommie74 on 2007-04-14
The problem is solved!

The following file needed to be changed:

/home/tommie/.gconf/desktop/gnome/url-handlers/http/%gconf.xml

```
<?xml version="1.0"?>
<gconf>
        <entry name="needs_terminal" mtime="1176124884" type="bool" value="false">
        </entry>
        <entry name="enabled" mtime="1176124884" type="bool" value="true">
        </entry>
        <entry name="command" mtime="1176124884" type="string">
                <stringvalue>/usr/lib/swiftfox/firefox &quot;%s&quot;</stringvalue>
        </entry>
</gconf>
```

I had installed swiftfox on my system, but removed it because it didn't seem any faster on my computer. So the line in the code above is pointing nowhere. Changing "swiftfox" for "firefox", saving and restarting did the job.

---

### Post by freebird54 on 2007-04-14
Makes sense I guess - though I don't know why setting the 'default browser' would not have picked that up.  Good find though!

I'll try to remember that for future reference  (ie: when it happens to me eventually :) )

---

### Post by tommie74 on 2007-04-14
Thx for helping me out!

---

### Post by NinerSevenTango on 2007-06-14
This worked for me.  Now, it might be helpful if we figured out what it was that broke the feature, since presumably the default install works as it should.  Perhaps it was Firefox itself, when I tried changing something in its own config, such as trying to force "open in new tab"?

--97T--

---

### Post by tommie74 on 2007-06-14
Hello 97T, 
this means that you didn´t install swiftfox and later on decided to uninstall it? Or any other webbrowser maybe?

---

### Post by NinerSevenTango on 2007-06-14
> **tommie74 said:**
> Hello 97T, 
this means that you didn´t install swiftfox and later on decided to uninstall it? Or any other webbrowser maybe?

Thanks for answering, Tommie.

No, I didn't.  I have been screwing and bumbling around trying to get multimedia files to 'just work', though.  Packages have been getting installed and uninstalled for that.  Plus, an update broke my X windows or whatever you call it, and I had to type in some other stuff to get it back.

Anyway, yesterday I copied that text into the config file, and it seemed to work OK.  Today, after a restart, the link opens in Firefox, but I get an error dialog box with this:  Configuration server couldn't be contacted: CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0

What the heck is that?

--97T--

Edit:  The smiley there is a colon followed by the letter "o".  LOL

Edit2:  I fixed all of the problems.  I used Synaptic to force reinstall of every package I could find related to Evolution, Corba, and gconf.  Then I went back into that file and pulled the extra text back out.  Then I rebooted.  Now it works as intended.

---

### Post by tommie74 on 2007-06-15
Well, I am quite new to linux, for about two months now. So I'm not an expert at all. I have no clue what might have caused your problem. I think though that it might have to do with changing about:config firefox settings as you suggested. You say you pasted the code I posted here in your gconf.xml file, did you backup? Maybe the old code can give some clues as to what might have caused the problem. Furthermore, if it was cause by changing firefox settings, you may try to force the problem occuring again by changing those settings back and forth once more... 
On the other side, you might as well keep enjoying you working system now without risking more trouble.. .  : )

---

### Post by mrhealthpatriot on 2008-07-08
Now swiftweasel 3 works when I click on a link in mozilla thunderbird. I just had to add a "3" to /swiftweasel/

---

