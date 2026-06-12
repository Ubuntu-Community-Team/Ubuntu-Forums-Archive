---
title: "[SOLVED] Two hopefully easily answered questions"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by philtbelfast on 2007-10-18
1) I downloaded the release candidate gutsy a few days ago, do I need to reinstall with the new gutsy released today or will update manager handle all that?

2) Fiddling about I removed whatever program is in charge of thumbnail previews for documents, for example pdfs or pictures on the desktop. Which program is this and can it be reinstalled with Synaptic?

Many thanks,

Phil

---

### Post by ThrobbingBrain66 on 2007-10-18
1) As long as you stay current with updates, you don't have to do anything special.

2) Previews are a part of Nautilus so it's not something you can unknowingly uninstall. Go to Edit > Preferences > Previews in Nautilus and re-enable previews for whichever file type you're missing them.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-18
1) chances are you have the final billed if you got the rc

---

### Post by philtbelfast on 2007-10-18
Thanks for the answer to 1 guys. Unfortunately no luck with 2.

Basically I had 4 pdfs on my desktop and their icons are only the standard document icon. Two days ago the icons were small previews of the actual pdf.

Quite confused, what could I possibly have done?

Many thanks,

Phil

---

### Post by Beggar on 2007-10-18
Does nautilus still open them with the right program? I.E. Can you double click them?

---

### Post by philtbelfast on 2007-10-18
> **Beggar said:**
> Does nautilus still open them with the right program? I.E. Can you double click them?

Yup they do.

---

### Post by Beggar on 2007-10-18
Then the only advice I can offer is check through nautilus edit->preferences as the previous poster said, make sure you have "other previewable files" set to local or always, and that the size limit is larger then the files you have created.

---

### Post by philtbelfast on 2007-10-18
Cheers guys, getting closer now! I cna now preview things like photos, but not pdfs, the preview size limit is set ridiculously high, so it cant be that,

Any more ideas?

---

### Post by Beggar on 2007-10-18
I had an idea, look in gconf and see what is registered for pdfs, run:

```
gconf-editor
```

navigate to /desktop/gnome/thumbnailers/

There should be an entry in this folder, application@pdf. 
If it is there then what is the command, and is the enabled flag set?

If it isnt there, try adding it, new string key name = "command" value="evince-thumbnailer -s %s %u %o", without the quotes.
also add boolean key name="enable", value is true. (in order to edit, you need to rerun with gksu gconf-editor)

Alternately, you could reinstall evince, probably the better solution, but I would like to confirm this is the issue, because there might be a bug somewhere.

---

### Post by philtbelfast on 2007-10-18
Bingo, evince was the problem, I got xpdf and assumed i didnt need evince anymore. Went back and installed it again, worked a treat!

Cheers for sticking with this.

---

