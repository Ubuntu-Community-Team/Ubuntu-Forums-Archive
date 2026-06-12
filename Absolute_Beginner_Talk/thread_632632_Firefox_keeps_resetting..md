---
title: "Firefox keeps resetting."
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by DaraJava on 2007-11-23
Sometimes, when I turn off my laptop, Firefox "resets".

That is to say that:

[LIST]
[*]All my settings are reset, e.g. my homepage is set back to the Mozilla-Google page, all privacy settings are reset, etc.

[*]All my bookmarks are deleted.

[*]All *add-on* settings are reset.

[*]Theme is set to default again.
[/LIST]

There are however things that don't change:

[LIST]
[*]Saved passwords

[*]Cookies

[*]I still have my add-ons and themes
[/LIST]

There might have been a thing or two on either list that I've forgotten but thats the general gist.

I also installed Swiftfox recently. I don't think it has anything to do with it but it could.

If I could get any help it would be great,
Thanks,

DaraJava.

---

### Post by dips_xe on 2007-11-23
the first thing i would try is to

sudo apt-get purge firefox

then reinstall it. you could uninstall swiftfox as well to eliminate it as a possibility..

---

### Post by DaraJava on 2007-12-01
Seems to have solved it. Thanks!

---

### Post by DaraJava on 2007-12-05
I posted this recently and thought it was solved. I marked the thread as [SOLVED] so I couldn't post there. 

Someone on that thread told me to uninstall Firefox and Swiftfox and reinstall it. I could not uninstall Swiftfox but I reinstalled Firefox and it seemed to be working for a while... and then it reset again. 

If anyone knows how to uninstall Swiftfox or if anyone has any other ideas on my problem it would be great.

Thanks, 

DaraJava

 
This was my original problem:
> 
Sometimes, when I turn off my laptop, Firefox "resets".

That is to say that:

[LIST]
[*]All my settings are reset, e.g. my homepage is set back to the Mozilla-Google page, all privacy settings are reset, etc.

[*]All my bookmarks are deleted.

[*]All *add-on* settings are reset.

[*]Theme is set to default again.
[/LIST]

There are however things that don't change:

[LIST]
[*]Saved passwords

[*]Cookies

[*]I still have my add-ons and themes
[/LIST]

There might have been a thing or two on either list that I've forgotten but thats the general gist.

I also installed Swiftfox recently. I don't think it has anything to do with it but it could.

If I could get any help it would be great,
Thanks,

DaraJava.

---

### Post by ccprog on 2007-12-05
This is just a wild guess, but it reminds me of an effect I encountered some time ago. My settings were lost, just as you describe. I could pin down the effect on Firefox closing unexpectedly. What seemed to happen was this:

- Firefox aborted, it seemed in the middle of writing the file %HOME/.mozilla/firefox/...(profile folder).../localstore.rdf
- On restart of firefox, since the file was missing, it restored the default version of that file.
- Since localstore.rdf hold links to a lot of profile settings, a number of files in the same folder were overwritten as a result. Mind you, until restart they still existed unmodified.

I was only able to patch this by saving a backup copy of the file. Unfortunately, this method depended on guessing whether something was wrong before starting Firefox. As soon as it was started, a lot of information was lost ultimately.

---

### Post by soliton on 2007-12-06
I have met the exactly the same problem :(

---

### Post by disturbedite on 2007-12-06
permission problem perhaps?  if changes (such as settings/bookmarks) aren't saved, then perhaps its cuz you don't have write permission.

---

### Post by aysiu on 2007-12-06
Try closing Firefox, typing this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username*:*username* /home/*username*/.mozilla
``` where *username* is your actual username, and then restarting Firefox.

---

### Post by DaraJava on 2007-12-06
Great! Thank you all. I have tried that last solution aysiu, Seems good but I won't mark this thread as [SOLVED] just yet. 

Thank you,

DaraJava.

P.S. Thank you for merging my threads and marking it unsolved. This forum is brilliant! Best one I ever saw. Good job!

---

### Post by aysiu on 2007-12-06
> **DaraJava said:**
> Great! Thank you all. I have tried that last solution aysiu, Seems good but I won't mark this thread as [SOLVED] just yet. 

Thank you,

DaraJava.

P.S. Thank you for merging my threads and marking it unsolved. This forum is brilliant! Best one I ever saw. Good job!
Why don't we go ahead and mark it as solved for now? And if that doesn't turn out to be a permanent fix, we can always unmark it.

---

### Post by DaraJava on 2007-12-07
:lolflag: Brilliant!

---

### Post by DaraJava on 2007-12-12
[UNSOLVED]

It didn't work. My firefox has reverted to it's original settings again. Any ideas?

---

