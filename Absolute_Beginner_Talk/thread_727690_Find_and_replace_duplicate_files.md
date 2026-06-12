---
title: "Find and replace duplicate files"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-18
I have many redundant mp3s on my external HDDs. Is there some way to find and eliminate them?

---

### Post by Rocket2DMn on 2008-03-18
There is a program called fdupes which should serve your purpose.  Read more here: [http://ubuntu.wordpress.com/2005/10/08/find-duplicate-copies-of-files/](http://ubuntu.wordpress.com/2005/10/08/find-duplicate-copies-of-files/)
There must be some way to have it only do mp3s, either through a script or piping output from "ls" or something like that.  I'm sure you can get creative :)

---

### Post by ShodanjoDM on 2008-03-18
I never tried this on external storage devices, but I use slocate.
```
sudo aptitude install slocate
```
You have to start indexing (manually) first before searching:
```
sudo slocate -u
```
And then just type:
```
slocate *.mp3
```

---

### Post by sayakb on 2008-03-18
What exactly does slocate do? I went to the external HDD's prompt (/media/Glade/music) and there I typed slocate *.mp3
The command didn't return any output and nothing happened.

---

### Post by sayakb on 2008-03-18
> **Rocket2DMn said:**
> There is a program called fdupes which should serve your purpose.  Read more here: [http://ubuntu.wordpress.com/2005/10/08/find-duplicate-copies-of-files/](http://ubuntu.wordpress.com/2005/10/08/find-duplicate-copies-of-files/)
There must be some way to have it only do mp3s, either through a script or piping output from "ls" or something like that.  I'm sure you can get creative :)

fdupes and fslint seem to be really useful. Thanks a lot for the link :)

---

