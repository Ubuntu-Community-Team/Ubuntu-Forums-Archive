---
title: "file permissions"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-06-17
i want to change the permissions of a directory and all of its contents. i know part of the command to do it, but i dont know what switch to use.

```
sudo chown USER PATH_OF_FILE
```

what am i missing

ps i meant change the ownership of the directory and its contents

---

### Post by hyper_ch on 2007-06-17
```

sudo chown -R user.group /path/to/dir

```

And you can also use:

```

man chown

```

---

### Post by k33bz on 2007-06-17
thanks :)

---

