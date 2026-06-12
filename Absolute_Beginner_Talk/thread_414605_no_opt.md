---
title: "no /opt"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Billy McCann on 2007-04-20
Howdy.  

I have no /opt on / .  

Screenshot below.  

#

---

### Post by nereid on 2007-04-20
Why don't you create one then?

```

sudo mkdir /opt

```

Should do the job, just check the permissions with *ls -l /opt*. Permission should be 755.

---

### Post by Billy McCann on 2007-04-20
> **nereid said:**
> Why don't you create one then?

```

sudo mkdir /opt

```

Should do the job, just check the permissions with *ls -l /opt*. Permission should be 755.


Sounds simple enough.  


Just wondering why my Feisty's a freak.  

 ```
                    _____
                ___/     \___
               `-._)     (_,-`
                   \O _ O/
                    \ - /
                     `-(
                      ||
                     _||_
                    |-..-|
                    |/. \|
                    |\__/|
                  ._|//\\|_,
                  `-((  ))-'
                   __\\//__ gnv
                   >_ /\ _<,
                     '  '



```

---

### Post by llamakc on 2007-04-20
it isn't a freak. Create the directory if you need it.

---

