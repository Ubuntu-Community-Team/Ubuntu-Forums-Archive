---
title: "user lost admin rights by itself"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Foudre on 2006-10-19
I WAS SOO HAPPY TO GET BACK ON KUBUNTU. ONLY TO BE CRUSHED THAT I COULDN'T GET ONLINE.

so what do i do, i go to system settings networking, both my ethernet adapter and my wireless are disabled, i try to goto advanced view
says su error or something like that, 
i try the wireless assitant, same thing
i go to the terminal type in sudo
it returned some sort of error (can't rember, but basicly that i don't have the rights to use sudo)


now why would my user account suddenly become not admin? I mean i was happy about getting my linux back, was going to post the success and thank bulldog, btw thanks, but ahh, I can't do anything without the rights to do them.

hummm, ya It raised my hopes and dashed the expediantly, bravo that was brilliant good blow computer. lol why is it the desktops i've built never have these problems, but laptops and ones i don't build seam to hate me?

am at a loss here, whey would i loose my admin rights? i'm the only one that uses this computer too

---

### Post by bulldog on 2006-10-19
If you go to administration -->Users and Groups can you get in there?

You need your password so...............

I suppose this can be repaired,only I don't know how,should somebody come by with some expertise on this subject.

---

### Post by Foudre on 2006-10-19
it lets me look at all the stuff in there, i just can' edit anything

---

### Post by jordanmthomas on 2006-10-19
You'll have to reboot in recovery mode and type this:
```
adduser *your_username* admin
```
Then, you should be allowed to use sudo again.

---

### Post by aysiu on 2006-10-19
jordanmthomas is correct.

More detailed instructions here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by Foudre on 2006-10-19
aie, no joy, when i did that it said i was already part of admni group, and i even made a new user added him to admin, same thing, i'm thinking i should just reinstall, besides my open office has been broken since install anyways and won't let me touch it, even if i reinstall package still won't load, so i guess i'll just reinstall, i have all my music i want on a dvd now, there are a few pictures but i can deal with loosing them, and a broken wine (lol i screwed around with it too much now i can't use windcfg) so oh well

---

### Post by M7S on 2006-10-19
I have twice had problems with not being able to use sudo on my laptop. My laptop seemed to forget it's hostname and that resulted in sudo not working. Is your hostname correct?

---

