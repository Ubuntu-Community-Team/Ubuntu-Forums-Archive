---
title: "Installing Chkrootkit - 0.47"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by keith1 on 2007-09-10
I'm new to this so bear with me please. I've been learning how to do so much, this kind of got put on the back burner. Since it's been awhile, I don't remember the steps I took to get where I'm at. So.... I'll just tell you where I'm at right now, and hopefully it's enough info to help me. If I need to start over from scratch, that's fine.

What I have now is a ( white ) folder on my desktop titled " chkrootkit 0.47. I may have downloaded, but not installed maybe? I've read that a rootkit is more dangerous to Linux than a virus - so it's time for me to pull the brakes on, and ask for help.


Thank you,    Keith

---

### Post by por100pre1 on 2007-09-10
Do this instead (in terminal):

```
sudo aptitude install chkrootkit rkhunter
```

To use them:

```
sudo chkrootkit
```

```
sudo rkhunter --update && sudo rkhunter -c -sk
```

Happy hunting! :)

EDIT: By the way, welcome to the forums!

---

### Post by keith1 on 2007-09-10
Thank you very much, I'll give it a try and post back my results on this thread.

Keith

---

### Post by keith1 on 2007-09-10
That did it!  Thank you, and I did come up clean on the scan. This is a great forum.



Keith

---

### Post by por100pre1 on 2007-09-10
Glad to help! 8)

---

