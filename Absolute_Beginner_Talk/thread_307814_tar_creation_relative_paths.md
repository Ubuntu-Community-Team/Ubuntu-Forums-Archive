---
title: "tar creation relative paths"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by Seine on 2006-11-27
Hi.

How can I create a tar file with paths relative to some base path.

E.G. I'm in /tmp and I create a tarball with everything under /home/bob, but I don't want /home/bob in the path of the tar entries.

I searched the manpage but didn't see a suitable option. (-P looked good but seemed to make no difference).

Cheers
Seine

---

### Post by Bachstelze on 2006-11-27
```
sudo -i
cd /home
tar czf bob.tar.gz bob/
```

Is that what you want ? I'm not sure I got it properly...

---

### Post by Seine on 2006-11-27
Yes, sort of.

Actually i just found my own answer. If I want relative paths, I have to use relative paths! *doh*.

```
jem@fawkes:/tmp/testingbackup$ tar czvf fruit.tgz ../fruit/
tar: Removing leading `../' from member names
../fruit/
../fruit/banana
../fruit/orange
../fruit/apple
../fruit/nectarine
../fruit/canteloupe
jem@fawkes:/tmp/testingbackup$ tar -tf fruit.tgz 
fruit/
fruit/banana
fruit/orange
fruit/apple
fruit/nectarine
fruit/canteloupe

```

Is what I was after, compared to

```
jem@fawkes:/tmp/testingbackup$ tar czvf fruit2.tgz /tmp/fruit/
tar: Removing leading `/' from member names
/tmp/fruit/
/tmp/fruit/banana
/tmp/fruit/orange
/tmp/fruit/apple
/tmp/fruit/nectarine
/tmp/fruit/canteloupe
jem@fawkes:/tmp/testingbackup$ tar -tf fruit2.tgz 
tmp/fruit/
tmp/fruit/banana
tmp/fruit/orange
tmp/fruit/apple
tmp/fruit/nectarine
tmp/fruit/canteloupe

```

I didn't want the 'tmp' in there.

Thanks
Seine

---

