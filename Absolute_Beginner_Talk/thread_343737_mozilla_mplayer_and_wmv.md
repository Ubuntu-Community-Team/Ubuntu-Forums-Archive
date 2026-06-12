---
title: "mozilla mplayer and wmv"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by andshoesandsocks on 2007-01-21
i have quicktimes running perfectly in my mplayer on mozilla but wmv's wont show up. how do i get them to work? thanks.

---

### Post by riven0 on 2007-01-21
Well, I'm not sure about mplayer, but I do konw that VLC supports WMV files. Have you tried installing that with all the plugins yet?

---

### Post by RomeReactor on 2007-01-22
Hi. Do you know if you have w32codecs? If not: **1.-** Open Synaptic (System-->Administration-->Synaptic Package Manager) and search for them:

```
w32codecs
```

If it fails to find them: **2.-** Perhaps you don't have the correct repositories enabled. Close Synaptic, open a Terminal (Applications-->Accessories-->Terminal) and write:

```
sudo gedit /etc/apt/sources.list
```

When Gedit opens, add at the end:

```
## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
```

Save and close Gedit. **3.-** Now open Synaptic again, click on "Settings--->Repositories" and check all boxes. Next click on the "Reload" button, and when it finishes, look for w32codecs again.

(Note: i can't remember if w32codecs are in the PLF repositories, so you may want to go from step 1 to step 3 and then try searching for the codecs again; if that doesn't work, apply step 2, open Synaptic again, press the "Reload" button, and search again).

(Note 2: Sorry for the long post :rolleyes: )

---

