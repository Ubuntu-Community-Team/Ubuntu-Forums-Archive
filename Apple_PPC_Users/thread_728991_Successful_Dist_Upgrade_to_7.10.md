---
title: "Successful Dist Upgrade to 7.10"
date: 2008-03-19
forum: Apple PPC Users
---

### Post by avtolle on 2008-03-19
I had been delaying upgrading from 7.04 to 7.10 on my G4 Cube, due to the various problems reported. Luckily for me, I was recently the beneficiary of another Cube that I could use to experiment.

After a clean install of 7.04 on the "new" Cube (after increasing its RAM to 512), and updating to current, I took the plunge and clicked on the button to upgrade to 7.10. The install was uneventful, and upon completion, restarted. At that point, I was dropped into intramfs. Following the suggestions posted on the forum, I typed in:
```

modprobe ide-core
exit

```to finish booting, then added
```

ide-core

```to both /etc/initramfs-tools/modules and /usr/share/initramfs-tools/modules, then ran the command
```

sudo update-initramfs -u

```and thereafter all was good.

Emboldened by this success, I did a distribution upgrade on my production machine two days later. The only difference was that in the latter case, there was no need to enter the above, as it booted upon restart without any complications.

Even though the release of Hardy looms next month, better late than never, I guess. Wanted to report my success, and to give thanks to the various posters who have posted on the Forum for their assistance.

---

### Post by stream303 on 2008-03-21
Thanks for the report!  It is very rare to hear from a cube owner..

---

