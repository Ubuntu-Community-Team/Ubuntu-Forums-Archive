---
title: "Can't find ccsm in gutsy!!"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by ryanxdurst on 2007-10-19
Hey, I just did a fresh install of gutsy, and I know that compiz fusion is already installed with it.  Now I need to install ccsm. I've read that it's supposedly in the repos, but i still can't find it. I tried " sudo apt-get install compizconfig-settings-manager" but it's not there. Thanks for any replies.

---

### Post by FuturePilot on 2007-10-19
Make sure you have all the repos enabled. It should be there.

---

### Post by dasunst3r on 2007-10-19
The package you are looking for is *compizconfig-settings-manager*.

---

### Post by ryanxdurst on 2007-10-19
Yeah, I didn't realize that you had to enable the repos manually, so I did that, but there were only three.  Also, I just realized that it's not just ccsm, I can't install ANYTHING.  I just read that some people are having problems with the repos? Does anyone know how to fix this?

---

### Post by dasunst3r on 2007-10-19
Where are you having trouble with the repos?  If it is in retrieving the packages, then do remember that the Ubuntu servers are a madhouse with all the people trying to upgrade to Gutsy right now.  If this is the case, you should consider using another mirror:[LIST]
[*]Go to System -> Administration -> Software Sources
[*]Under "download from," choose the server closest to you.
[*]Make sure all the repositories are checked
[*]Close out, open a terminal, *apt-get update*.[/LIST]

---

### Post by ryanxdurst on 2007-10-20
Ok, it all works now since i switched mirrors. Thanks a lot!

---

### Post by Dr Small on 2007-10-20
Please remember to mark your theads as solved from Thread Tools.
Thank-you :)

---

