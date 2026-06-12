---
title: "how does it start up?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by davaca on 2006-06-19
so... I have inbstalled ubuntu, but I don't know how to start it. I put my pc on, choose ubuntu (I also use XP, on which I am right now), and get some DOS-like thing, asking my login and pasword. I fill them in, and then I get a small explanation on sudo (or something like that) and some prompt. I really don't know how to start it up right

---

### Post by [S|G] on 2006-06-19
Usually Ubuntu already starts on graphical mode, it sounds like you have some broken video drivers (or have done a server install of ubuntu). After logging in, try typing "startx" and post any message you get here.

---

### Post by davaca on 2006-06-19
it says it doesn't know the command...

however, I think it's best if I just reïnstall it properly... the server thing is probably right, where can I find the right version?

---

### Post by [S|G] on 2006-06-19
Just let it install with default options and you should have a desktop computer installed. You probably chose a server install somewhere on setup.

But there is no real need to re-install if you don't want to. You can type this:
```

sudo apt-get install ubuntu-desktop

```
And it will install the files from the desktop system.

---

### Post by davaca on 2006-06-19
with the cd inside?

---

### Post by [S|G] on 2006-06-19
If the CD is inside it'll fetch the files from it, I believe. However you can do that without the CD and it'll fetch the files from the internet. If you have a fast internet connection and some time to spare, you'd be better off downloading the updated packages.

---

