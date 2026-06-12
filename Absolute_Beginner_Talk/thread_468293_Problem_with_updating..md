---
title: "Problem with updating."
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by bvanga on 2007-06-08
I have Ubuntu 7.04 installed...Its been working fine but recently i can't update, the updates in update manager. It looks like it downloads the files but just don't update, I try just checking one update and trying it and it still doesn't work. thanks in advance!

---

### Post by NeoLithium on 2007-06-08
Have you tried using the command line? Open up a terminal window (Applications -> Accessories -> Terminal) and type in
```

sudo aptitude update

```
Let it do it's thing, and then:
```

sudo aptitude upgrade

```

If it works, great, if not, it will give you error messages you can post so we can see what's up with it :)

---

