---
title: "Does anyone know how to Blacklist a certain application using 'aptitude'"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-03-02
I often use aptitude to upgrade my packages and there is one package I would like to lock from updating. I've locked it in Synaptic but not sure how the command works in 'aptitude'. Suggestions will be appreciated.

---

### Post by eXisor on 2007-03-02
sudo aptitude hold <packagename>

To get the full list of aptitude commands, type 'man aptitude'

---

### Post by Bagboy23 on 2007-03-02
Done. Thanks.

---

