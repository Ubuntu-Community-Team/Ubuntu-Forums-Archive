---
title: "ubuntu ppc repository 404"
date: 2010-10-10
forum: Apple Hardware Users
---

### Post by luvgirl12345 on 2010-10-10
Please help!! Every time I try and update this comes:

```

W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-powerpc/Packages.gz  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

```

Is this a known bug??

---

### Post by PeterBL on 2010-10-13
I get the same message. Don't know how to fix the problem. But it is definitely not only an issue for you.

---

### Post by zeroti on 2010-10-14
Well my guess is that the extras repository doesn't exist for powerpc users. (Although I may be wrong.) I looked at the software sources list that I had in Lucid, and I didn't find the word "extra" in it, so that seems to support my theory...

One way to remove it is to open the Update Manager under the System -> Administration menu and then to click the "Settings" button. Then select the "Other Software" tab and uncheck the software sources titled "Independent". Then click close and try updating, by clicking "Check" in the Update Manager. That should fix it.

If there does turn out to be such an extras archive for ppc, you can always add it back in. :)

---

