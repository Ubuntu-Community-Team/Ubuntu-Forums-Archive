---
title: "How can i reinstall ALSA back to 7.10 defaults"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Mauler5858 on 2008-04-02
I have messed up my alsa.  How can i restore it back to the defaults of Gutsy?

---

### Post by wolfen69 on 2008-04-02
go to synaptic and completely remove alsa. then:
```
sudo apt-get clean
```
then
```
sudo apt-get autoremove
```
then go back to synaptic and re-install.

---

### Post by Mauler5858 on 2008-04-02
And will the installation automatically re-recognize my sound card?

---

### Post by Elderlygent on 2008-04-02
Thanks Wolfen69, but in reinstalling how do I know which packages to include? There are a lot, although only two with Ubuntu logo.

Please specify.

---

