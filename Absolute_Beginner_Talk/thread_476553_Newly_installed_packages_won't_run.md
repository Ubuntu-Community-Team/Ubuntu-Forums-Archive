---
title: "Newly installed packages won't run"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-06-17
Using Synaptic Package Manager I installed Konqueror & KPDF and neither  of those applications will run. Using add and remove I installed Amarok and it won't run either. Anyone able to help me out here?

Thanx

---

### Post by dreadlord_chris on 2007-06-17
> **captgadget said:**
> Using Synaptic Package Manager I installed Konqueror & KPDF and neither  of those applications will run. Using add and remove I installed Amarok and it won't run either. Anyone able to help me out here?

Thanx

How are you trying to run them?
What is the error message when run from the terminal?

---

### Post by captgadget on 2007-06-17
It tells me they are installed. I got to applications>graphics>KPDF and nothing happens. I go to applications>internet>Konqueor and nothing happens.

---

### Post by jfoobar on 2007-06-17
I have had the same thing happen with Gnash SWF Viewer, but so far that is the only newly-installed application it has happened to.  The application addition through Synaptic went fine with no errors and it shows up as installed in Synaptic and shows up in my application menu but attempting to start the application results in nothing at all.

---

### Post by captgadget on 2007-06-17
Well, I guess no body has an answer to this one for us.

---

### Post by dreadlord_chris on 2007-06-17
> **captgadget said:**
> Well, I guess no body has an answer to this one for us.

in a terminal type:
```

kpdf

```
and tell me what the output is...

---

### Post by captgadget on 2007-06-17
It tells me it's not installed which I suppose is logical since I sudo apt-get remove kpdf

---

### Post by captgadget on 2007-06-17
I reinstalled in terminal. Typed in kpdf and got this:bash: kdpf: command not found

---

### Post by captgadget on 2007-06-17
Then I did sudo kpdf and got this:sudo: kdpf: command not found

---

### Post by jfoobar on 2007-06-17
kpdf is not installed on my system.

---

### Post by dreadlord_chris on 2007-06-18
> **captgadget said:**
> I reinstalled in terminal. Typed in kpdf and got this:bash: kdpf: command not found

That's really weird - could you post the output of:
```

sudo apt-get install kpdf

```

---

### Post by rajgerman on 2007-08-16
Hi,

I'm new to ubuntu and I have a similar problem where gnash swf viewer is installed. It doesn't load from Applications->Sound&Video->Gnash SWF viewer. From the terminal when I try to play a swf file the player comes up but nothing plays. Any suggestions?

Thanls.

---

