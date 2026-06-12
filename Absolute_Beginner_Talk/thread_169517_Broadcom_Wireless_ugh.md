---
title: "Broadcom Wireless *ugh*"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by nsabatino on 2006-05-02
Hi all,

I've been following this [guide]("http://www.ubuntuforums.org/showthread.php?t=25683") for installing the wireless on my Averatec 3220H1.

Worked well untill i had to enter in this bit:
```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```

I got:
```
nsabatino@nick2:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4301.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4307.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4321.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied

```

Any ideas? Is it something simple that I'm doing wrong?

Thanks,
-Nick Sabatino

---

### Post by Nequeo on 2006-05-02
[QUOTE=nsabatino]Hi all,

I've been following this [guide]("http://www.ubuntuforums.org/showthread.php?t=25683") for installing the wireless on my Averatec 3220H1.

Worked well untill i had to enter in this bit:
```
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
```

I got:
```
nsabatino@nick2:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4301.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4307.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4321.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied

```

Any ideas? Is it something simple that I'm doing wrong?

Thanks,
-Nick Sabatino[/QUOTE]

I seem to recall reading somewhere that sudo works non-intuitively when combined with file redirection. Try typing 'sudo -i', which should give you a root prompt, and then repeat that command (but without sudo, of course). 

May not help, but off the top of my head that's my best guess. 

I hate Broadcom cards.

---

