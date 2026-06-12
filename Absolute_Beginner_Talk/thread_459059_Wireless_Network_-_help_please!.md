---
title: "Wireless Network - help please!"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Steven_Gerrard on 2007-05-30
Hello! I have dual-boot windows xp and ubuntu feisty. My problem is this: if I run windows, the wireless is fine. But about half of tthe times when I start in ubuntu, the wireless simply doesn't work. Any thoughts on how to make it (more) stable?

Thanks in advance.

---

### Post by Inxsible on 2007-05-30
Can you give us a bit more info, as to what the errors are, if any?
 
What wireless card do you have?
You say it works half the time? Do you do anything different the other half ?
Do you have a secured network? If yes, which one?

---

### Post by Steven_Gerrard on 2007-05-30
No, stupidly I haven't got a secured one. Hmm, usually it doesn't automatically work when I start up. I have three different networks in reach, so when I press the one that doesn't work, about 50% it works. When it doesn't work, I have to reboot, which gets annoying after a while. Telenor, and router from jensen scandinavia. This probably sounds stupid, but I'm not sure what kind of card I've got, any way to check?:P Thanks for the interest.!

---

### Post by Sparkster185 on 2007-05-30
You can type

```

lspci -v | less

```

and scroll through the output.  If you search the word "Ethernet" (by pressing '/' then typing the word), you should find it.  To skip to the next search result, press 'n'.

---

