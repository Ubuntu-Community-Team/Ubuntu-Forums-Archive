---
title: "Feisty upgrade killed my system"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by robertje on 2007-03-28
I just tried to upgrade my Dell D600 to Feisty, and I may need to reinstall (yes, all has been backed up, no real big deal). I replaced "edgy" by "feisty" in the repositories file, ran apt-get update, apt-get upgrade, apt-get dist-upgrade. That went fine; after a reboot my wireless was dead though, and it also killed my wired networking. Then I reconfigured the wired networking (wireless I disabled), and the system crashed unexplainably. Rebooting left me with a shell only but the wired networking worked now. apt-get update, apt-get upgrade, apt-get dist-upgrade, and then a reboot, and now everything is broken (kernel panic or a boot stop; no shell). XP still works like a charm.

Does anyone perhaps have a suggestion for avoiding a reinstall?

---

### Post by deathbyswiftwind on 2007-03-28
Hi well I dont know the solution to your problem you should have posted this under the development section. Youd stand a better chance since feisty is still in development.

---

### Post by igknighted on 2007-03-28
If you still want feisty do a clean install.  I can't promise no issues, but I think the problems you did have were due to the upgrade (which is spotty at best... clean install is always the way to go).  Once Ubuntu releases hit beta they are usually OK for most users who know Ubuntu well.  New users should wait until a week or so after official release still.  But if you are comfortable fixing minor things that go wrong, give the beta a try (at this point the major issues should be past).  If you need stability right now stick with edgy, but when fiesty comes out I would recommend another clean install.

---

