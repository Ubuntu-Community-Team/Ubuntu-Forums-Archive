---
title: "need help with custom kernel compile, using git and patch for Speakup (blind users)"
date: 2008-08-10
forum: Assistive Technology &amp; Accessibility
---

### Post by dennister on 2008-08-10
When I recently built a kubuntu & Ubuntu system for a blind user, using hardy 8.04.1, I got Orca and kttsmgr working right away, but these options not only make the system too sluggish (he is buying more rambus memory for orca), the limited amount of information they read from the gui screen make it very difficult to use. Please note that he's used to jaws for windows, and has a sighted girlfriend who'll also be using the pc, so this is why we left the gui on. He'd also like the option of using the gui for the things gui-based screen readers can do well.

However, what he really wants and needs is a screen reader that will work in console, and thus in konsole within the gui. He and I are in full agreement with Karl Dahlke, author of edbrowse and this article: [http://eklhad.net/cli.html](http://eklhad.net/cli.html) 

Long live the commandline!

One issue is that hardy has dropped repository support for Speakup, Speak-freely is likewise not supported, and neither is any other console-based screen reader I can find. Yasr is almost useless because documentation is almost non-existent. To make matters worse, Speakup requires the kernel to be patched, (synthesizers as modules) which I have done, as well as installed speech-dispatcher, speechd-up, several synthesizers that were pulled in as dependencies...They're all running, and I've edited as many conf files as I could find.

Some help here would really be appreciated. I'd like to do it here on my machine over the next day or two, and then duplicate the work on his machine when I go over there to get their network going on Thursday.

Thanks in advance!

---

### Post by SkullKill on 2008-11-06
We did get the same problem as you got. And due to the lack of documentation online, it was very hard. we were finally able to make it work after a longggg list of errors and problems.

anyway, be cause of the lack of documentation, we decided to put our work online. it is our 1st guide, so. if you have any questions, we will try to answer them.

the guide is at
[http://sites.skaccess.com/speakup/]("http://sites.skaccess.com/speakup/")

Hope that helps

p.s there is also a precompiled kernel with speakup patch. it available for download at the site. it has DoubleTalk configured by default, but you can modify what module to load under grub boot file.

---

