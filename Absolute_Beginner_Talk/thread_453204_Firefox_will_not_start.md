---
title: "Firefox will not start"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by scottvan on 2007-05-24
I am using Feisty 7.04 and was changing fonts in Firefox 2.0.  Firefox just disappeared and will not start.  I tried uninstalling and reinstalling it, rebooting Ubuntu, but it still won't start.  Running Firefox from the terminal I get the following output:

Floating point exception (core dumped)

Any ideas on what to do (other than reinstalling Ubuntu)?  I am using Opera to write this...

---

### Post by Jussi Kukkonen on 2007-05-24
Your profile probably has problems. The easiest way to test is to try starting Firefox with a new profile:
```
firefox -ProfileManager
```
The old profile may be fixable, but it might be easiest to just use the new profile and import bookmarks and such...

---

### Post by Viskovitz on 2007-05-24
When you uninstalled in Synapric, did you chose "remove completely"? Try it and then reinstall.

- OR -

It's a very weird thing, but if it's due to a certain configuration in firefox, it should be stored in  your preferences folder. Try this:
```

rm -rf ~/mozilla/firefox/

```
and then run firefox again from the command line. Did it make a change?

---

### Post by Viskovitz on 2007-05-24
Oops, just trust Jussi :)

---

### Post by scottvan on 2007-05-24
> **Viskovitz said:**
> When you uninstalled in Synapric, did you chose "remove completely"? Try it and then reinstall.

- OR -

It's a very weird thing, but if it's due to a certain configuration in firefox, it should be stored in  your preferences folder. Try this:
```

rm -rf ~/mozilla/firefox/

```
and then run firefox again from the command line. Did it make a change?
Thank you for the help.  I tried removing completely, then re-installing, but no change.  I tried "rm -rf ~/mozilla/firefox/" from the  terminal, but then after running firefox from the terminal, I get "Floating point exception (core dumped)" again.

---

### Post by scottvan on 2007-05-24
> **Jussi Kukkonen said:**
> Your profile probably has problems. The easiest way to test is to try starting Firefox with a new profile:
```
firefox -ProfileManager
```
The old profile may be fixable, but it might be easiest to just use the new profile and import bookmarks and such...
Well, that seems to work, I created a new profile and Firefox popped right up!  Thanks!!

---

