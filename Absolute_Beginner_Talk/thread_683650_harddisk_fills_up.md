---
title: "harddisk fills up"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by AlmaTlust on 2008-01-31
Somehow my harddisk fills up for no obvious reason. I don't copy stuff to it, but still every day there's about 500 MB (!) less on it. A few days ago 18GB were left, now it's only aroun 15.5GB. What could be the problem, and how can I solve it?
It seems to me that the problem occurs at boot time, although I don't know. 
I have a Sony Vaio PCG-K115S with 512 MB of RAM, and a 60GB harddisk.

---

### Post by emarkd on 2008-01-31
Have you tried searching for large files and trying to find the culprit?  Run:

```
gnome-search-tool
```

and search for 500MB+ files

You could also use find from the command line

```
find / -size +500M
```

I think....

---

### Post by taurus on 2008-01-31
Do you happen to have a cron running that makes a backup of your system everyday?  Look in /var/backup.

```
sudo du -h /var/backup
```

---

### Post by AlmaTlust on 2008-01-31
Thank you for the tips. . I used konqueror and searched for files bigger than 10MB that were created in the last two weeks, and got the following list:

file:///var/cache/apt/archives/scribus-svn_1.3.5%7Esvn20080116-1_i386.deb
file:///var/cache/apt/archives/smc-data_1.4-1%7Egutsy1_all.deb
file:///var/lib/clamav/clamav-f037cadd84923b309ddae2dfee8cacc6/main.ndb
file:///var/lib/clamav/clamav-36b3452efb64aaca4e74f12cbd976712/main.ndb
file:///var/cache/apt/archives/kdebase-workspace-data_4%253a4.0.0-0ubuntu7%7Egutsy1%7Eppa1_all.deb
file:///var/lib/clamav/clamav-13053e9b6d933ceac8e3eeaf2cd772b6/main.ndb
file:///var/lib/clamav/clamav-ac1e3f1b99404fed0c6a528d7ede8587/main.ndb
file:///var/lib/clamav/clamav-07e875af63cfb0a4daf8faafc17cea07/main.ndb
file:///var/lib/clamav/clamav-cb82544ec099a959093683c0a3c57f2a/main.ndb
file:///var/lib/clamav/clamav-34f0c5452ce2dd2226d3080121b0eddc/main.ndb
file:///var/lib/clamav/clamav-89e6b4e16e07560b07558ea28b6a2d96/main.ndb
file:///var/lib/clamav/clamav-1581444f4b10689ddf45a457bfcfb567/main.ndb
file:///var/lib/clamav/clamav-c07eb8f106bdc0d1379105f4e82614d2/main.ndb
file:///var/lib/clamav/clamav-43656d38b8d96183b69897a934adbc43/main.ndb
file:///var/lib/clamav/clamav-696de6a3bfa6481c1fe745d4822f1261/main.ndb
file:///var/lib/clamav/clamav-65d7b7797cc0f935e7b102aae3a723c6/main.ndb
file:///var/lib/clamav/clamav-7a98e8c9274dd705d49e8e5a10427051/main.ndb
file:///var/lib/clamav/clamav-896250ec53017cb511e66638faedd888/main.ndb
file:///var/tmp/kdecache-martin/kpc/kde-icon-cache.data
file:///var/lib/clamav/clamav-dc3d43a0f03160004b992604b57e8bf4/main.ndb
file:///var/crash/_usr_bin_scribus-ng.1000.crash
file:///var/lib/clamav/clamav-7e2925c047781564d07836e8e10b0d31/main.ndb
file:///var/lib/clamav/clamav-e0c3e9392483687c7738bf02d2238026/main.ndb
file:///var/lib/clamav/clamav-ccb442900e31558448e4fbd7a29d8583/main.ndb
file:///var/lib/clamav/clamav-cebd594c59fe469069b55c07da00f8c4/main.ndb
file:///var/lib/clamav/clamav-2e3594d0d333daa389c1ff89649627b4/main.ndb
file:///var/lib/clamav/clamav-b396113ef481aac96052872ba39e39ee/main.ndb
file:///var/lib/clamav/clamav-49458c41f7ba3628593fcd357f04d99d/main.ndb
file:///home/Kinder/.jagex_cache_32/runescape/main_file_cache.dat2
file:///var/lib/clamav/clamav-dce10ed4031fcb99e7361fabe2379daf/main.ndb
file:///var/lib/clamav/clamav-b7f7dc42afa15be385254ce0675257eb/main.ndb
file:///var/lib/clamav/clamav-dd676f462ece6a917f79ff4d0b0230f1/main.ndb
file:///var/lib/clamav/clamav-14bb81b856cdc7cf8c94327cb286e958/main.ndb
file:///var/lib/clamav/clamav-a15007467470ad33ff97557362c6094c/main.ndb
file:///var/lib/clamav/clamav-3f26d2e9b073cfa27d5097eb9dd17d06/main.ndb
file:///usr/share/icons/crystalsvg/icon-theme.cache
file:///var/lib/clamav/clamav-0f0d17668982d9c40b22d262a79c2e34/main.ndb
file:///home/martin/Downloads/getskype-linux-deb
file:///var/lib/clamav/clamav-84e6958e0fdb42867220be84adf5caab/main.ndb
file:///var/lib/clamav/clamav-28d7021968bfa7f50f87d9f88b5abb38/main.ndb
file:///var/lib/clamav/clamav-e4cf67275a3c86295d10c905192de97f/main.ndb
file:///var/lib/clamav/clamav-ff69b348c6e690cde64101d9e72b0b5b/main.ndb
file:///var/cache/apt/srcpkgcache.bin
file:///var/cache/apt/pkgcache.bin
file:///var/lib/clamav/clamav-41b48395faa05203edabfbe4474eecd8/main.ndb
file:///var/lib/clamav/clamav-12f2963f37e63230759226757e7dd8c3/main.ndb
file:///proc/6005/fd/4
file:///proc/6005/task/6005/fd/4
file:///proc/6005/task/6112/fd/4
file:///proc/6005/task/6113/fd/4
file:///proc/6005/task/6114/fd/4
file:///proc/6005/task/6115/fd/4
file:///proc/6005/task/6249/fd/4
file:///proc/6005/task/6250/fd/4
file:///proc/6005/task/6253/fd/4
file:///proc/6005/task/6309/fd/4
file:///proc/6005/task/6344/fd/4
file:///var/lib/mysql/ibdata1
file:///var/lib/clamav/clamav-dfa742abd231b49a81457a0bde5cd6c8/main.ndb
file:///dev/core
file:///proc/kcore
file:///dev/.static/dev/core
file:///lib/udev/devices/core
file:///sys/devices/pci0000%3A00/0000%3A00%3A00.0/resource0
file:///sys/devices/pci0000%3A00/0000%3A00%3A01.0/0000%3A01%3A05.0/resource0


So it seems that clamav is the troublemaker, as its files are about 14MB each. I will have to check how to deal with them. Thank you for your help!

---

### Post by hyper_ch on 2008-01-31
what do you need antivurs for anyway?

---

### Post by Cypher on 2008-01-31
You can also try setting your core size to 0 with
```

ulimit -c 0

```
to avoid creating a any large core files for programs that misbehave..

---

### Post by AlmaTlust on 2008-01-31
what are core files for? Any security issues or stuff?

---

### Post by AlmaTlust on 2008-01-31
I need the AV because my company demands I have one... ;-) (everything else works on Windows).

---

### Post by hyper_ch on 2008-01-31
> **AlmaTlust said:**
> I need the AV because my company demands I have one... ;-) (everything else works on Windows).

That sux :(

---

