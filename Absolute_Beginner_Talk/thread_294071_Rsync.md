---
title: "Rsync?"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by jimmyk on 2006-11-06
Hi,

I want to keep the contents of a folder on my university home file store (I have ssh access) up to date on my computer at home.  Currently I am using scp to overwrite all the contents of the folder, I was wondering if I would be able to use something like rsync to only update files that have changed?

Is this possible? If so could somebody point me in the direction of some information on how to do it.

Thanks,

James

---

### Post by xyz on 2006-11-06
These may help you out:
[http://ubuntuforums.org/showthread.php?t=274297](http://ubuntuforums.org/showthread.php?t=274297)
[http://sial.org/howto/rsync/](http://sial.org/howto/rsync/)

---

### Post by jimmyk on 2006-11-06
Wow! That was quick.

This seems exactly what I was looking for. Thanks

---

### Post by jimmyk on 2006-11-09
Just incase any body else wants to do this, here is how I got it working.

1. Installed rsync through synaptic on my ubuntu machine (it will also need to be installed on the remote machine)

2. Used the command:

```
rysnc [host]:/src_dir/ dest_dir
```

NOTE - I think the "-e ssh" option is no longer required.

This is miles quicker than over-writing all the files using scp.

Hope this helps somebody else

---

