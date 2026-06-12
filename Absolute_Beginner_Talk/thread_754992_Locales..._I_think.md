---
title: "Locales... I think"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by fonggiding on 2008-04-14
This is probably a really simple fix, but alas noobieness(sp) is at fault.

I want to start transitioning over from gui's to just the console(no X). I have a bunch of cool programs like mutt(e-mail), lynx(web browsing), and finch(chat) to assist me in my adventure. However I have one small problem: My system keeps trying to display the programs in Japanese(what I normally use), but Japanese characters don't work on the console without x. So I'd like to get the programs running in English.
 SUMMARY:

I want to make my programs run in English not Japanese in the console.
      or
I want to get Japanese characters to show in the console(this is probably impossible).

Thanks in advance!

---

### Post by RealPSL on 2008-04-14
I certainly think you are right about it being a locale problem. Have you tried setting the LANG variable to ```
LANG=en_US.UTF-8
``` to test out that theory?

---

### Post by fonggiding on 2008-04-15
Thanks for the speedy reply! I ended up changing the system(by use of the language tool in system>administration) and changed my default language to English. But now SCIM(a multiple language input system) doesn't work so I'll put the default language back and try it your way.

Well. I tried it. My SCIM is working but It still opens programs in Japanese which turns into a series of little diamonds. I ctrl+alt+F2 into tty2 and tried using LANG=en_US.UTF-8 but with no avail.

Maybe I should try to get SCIM working on English mode...

Thanks for the help.

---

