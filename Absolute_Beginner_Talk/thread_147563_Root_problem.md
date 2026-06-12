---
title: "Root problem"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by ignorance on 2006-03-20
well i'm using ubuntu for a 4 months now and i like it more in fact i didn't used windows since than anymore but i got a serious problem today.

```

root@Christophe:/home/christophe#

```

i know this isn't normal how come it's listed /home/christophe what happend or what did i triggered to let this happen?

---

### Post by earobinson on 2006-03-20
im not sure I understand your problem /home/christophe is just the current path

---

### Post by pbaehr on 2006-03-20
I don't know if I understand what you are expecting but I'll venture a guess that you are expecting a ~ in place of the full path? You are logged in as root, so it's not your home folder any more. If you log in as christophe it will display as ~ like normal.

If this isn't what's upsetting you about your prompt you'll have to be more specific. It's hard to understand what exactly is bothering you.

---

### Post by ignorance on 2006-03-20
it's the path name that's bothering me and the fact when i try to enter something in /etc/... it says the file doesn't exist so i gotten in my own path somehow and that i don't like as pbaehr said i need the ~, i know i can return the path by using cd but everytime i get to root i get the pathname, were i never had that in the past always giving me directly a ~.

---

### Post by earobinson on 2006-03-22
cut and paset exactly what you are doing along with the error msg

---

### Post by IYY on 2006-03-22
First of all, why are you logging in as root anyway?

Second, does this problem happen only when logged in as root?

---

### Post by LKRaider on 2006-03-22
There is no error there, this is normal behaviour.

Type "exit" and you should get back to regular user mode.

---

