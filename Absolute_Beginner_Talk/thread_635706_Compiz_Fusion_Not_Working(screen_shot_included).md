---
title: "Compiz Fusion Not Working?(screen shot included)"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2007-12-09
Ok so i've included a screen shot. i'm dual booting ubutnu gusty gibbon 7.10 and vista. help?

---

### Post by mevets on 2007-12-09
That name looks right. Any esay way to iinstall CCSM is to Go to Add/Remove and type "ccsm". Maje sure show "All available Applications" is selected.

If you dont see it you may want to runt his:
> 
sudo apt-get update


---

### Post by RadiationHazard on 2007-12-09
nothing showed up. Ok so i want to this one site and it told me to go to synaptic package manager search "compiz" and delete everything that showed up. so i did that. i probably screwed up really badly huh??:(:(:(

---

### Post by Natr0n on 2007-12-09
Click on the down arrow on the box in the upper right hand corner of the Add/Remove Applications window that says "Supported Applications" then select "All Availabe Applications" and repeat the search.

---

### Post by mevets on 2007-12-09
Yeah follow what nat says, I shoulda been more specific

---

### Post by Ub1476 on 2007-12-09
> **RadiationHazard said:**
> nothing showed up. Ok so i want to this one site and it told me to go to synaptic package manager search "compiz" and delete everything that showed up. so i did that. i probably screwed up really badly huh??:(:(:(

Yes, slightly. Just reinstall the Ubuntu-desktop:

```
sudo apt-get install ubuntu-desktop --reinstall
```

Then do as the above posts mention.

---

