---
title: "error in  removing  IPPLAN"
date: 2012-07-20
forum: Any Other OS
---

### Post by vykuntamsrinivas on 2012-07-20
hi all,i am using debian sid.I have installed  ipplan(google-chrome-stable_current_i386.deb) and it had showed some  dependency problems so i tried to remove it using command #dpkg  --remove,but it is giving the following error :
```

Removing ipplan ...
dpkg: error processing ipplan (--purge):
 subprocess installed post-removal script returned error exit status 10
Errors were encountered while processing:
 ipplan

```


i googled this error.I removed  [COLOR=#BF0040] set -e[/COLOR]  in  all  [COLOR=#0000FF]var/lib/dpkg/info/ipplan.* [/COLOR]  files and  then tried to purge ipplan.Its still giving the same error.any one please help me out?:guitar:

---

