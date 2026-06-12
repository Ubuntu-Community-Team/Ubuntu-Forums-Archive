---
title: "Feedback"
date: 2005-06-08
forum: BUM - Boot Up Manager
---

### Post by jayc on 2005-06-08
While I can't quote the GNOME HIG, I think these suggestions would a step closer to it.  Please take this as constructive criticism!  I'm not trying to be negative at all.

When it starts up and does "Please wait, loading data..." I don't think the font really needs to be red.  I don't know of any other application that does this.  Instead, you could use a progress bar.  If you can't easily estimate the time, you could use the one that bounces from side to side.  Red is very startling and not necessary.

I think even better than a separate dialog would be to put the text "Loading services..." into the TreeView while it loads.  Then once it's done loading, swap it out.

If you keep the dialog though, the version number shouldn't be in there.

When the services are listed, I think there should be three columns.  The first one how it is (checkbox), the next a description, and the third the actual daemon.  Most users using the tool aren't interested in what the executeable is called which is why it should be last.

And by prepending the daemon name to the description creates an awful staggering effect and makes the descriptions very unreadable.  When reading one entry to the next our eyes have to readjust each time to find where the text we want to read is.

File -> Exit should instead use the stock item Quit.  Same with Help -> About whose accelerator is non-standard.  The license entry is rather superfluous and non-standard.  The license is stated in the About dialog.

Also at the bottom I think the buttons should be:  [ Cancel ] [ Ok ] which are the right HIG buttons and go along with the other gnome-system-tools.

Also does everything need an accelerator?  I suppose there's not a lot of harm in it, but other GNOME applications only do them for the important ones so having one on every single one was kind of odd.

I know people have been really looking forward to a tool like this.  Thanks. :)

---

### Post by saltydog on 2005-06-10
Thank you for your kind suggestions. I will put them on a todo list for future release (next one is already done...)

Fabio

---

### Post by fordp on 2005-06-10
Just a short post to say that I came to this section expecting something like grubconf.

Maybe consider merging grubconf into this package ?

Just a thought.

---

### Post by saltydog on 2005-06-11
[QUOTE=fordp]Just a short post to say that I came to this section expecting something like grubconf.

Maybe consider merging grubconf into this package ?

Just a thought.[/QUOTE]

It could also be, but I think that the "scope" of BUM is completely different from that of grubconf.

---

### Post by virgule on 2005-06-20
Im running Ubuntu Hoary since last week, convert from YellowDog, and could not figure out how to setup startup services. Those weird 'hacks' like rm links in /etc/rdS.init_something/huh.conf are annoying me to say the least. BUM is spot-on. There is so much goodies around just waiting to be discovered..

I kindly request it be placed in apt-get MAIN repositories.

---

