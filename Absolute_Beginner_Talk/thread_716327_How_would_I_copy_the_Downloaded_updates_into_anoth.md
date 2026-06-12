---
title: "How would I copy the Downloaded updates into another computer?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by j_a_c_k_s_o_n on 2008-03-05
Hello, i do have 5 pc to be updated with new packages.. The problem is that i couldn't find the downloaded files that was done on my main computer...How I retrieve and transfer the files that been downloaded?

---

### Post by dstew on 2008-03-05
Can you update the systems on the other computers over the network?

---

### Post by dwanders on 2008-03-05
I have a much better Internet connection at work than I do at home. I run matching versions of Ubuntu on both, and in the past (I have not needed to do it recently - but specifically during the first build to get all the patches etc...) I would:

from the source
1) do apt-get update
2) do apt-get upgrade
3) once the upgrade was done, all the files are stored in /var/cache/archives, so I copied that entire folder to a thumb drive (2 gig) or if it was small enough burnit to a cd

to target
1) upload all the files to /var/cache/archive
2) run apt-get update
3) run atpg-et upgrade

seemed to work fine for me, everything I uploaded it did not need to be downloaded, and it save a ton of time. I am sure there are more graceful ways of doing it, but that worked for me.:guitar:

---

