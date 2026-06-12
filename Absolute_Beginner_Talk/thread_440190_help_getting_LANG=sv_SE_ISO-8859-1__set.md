---
title: "help getting LANG=sv_SE ISO-8859-1  set"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by janne5011 on 2007-05-11
Hi I tried to install this from root shell
LANG=sv_SE ISO-8859-1
like this:
export lang=LANG=sv_SE ISO-8859-1
but it says ISO-8859-1 isnt valid or soemthing like that.
is ISO-8859-1 missing how do I get it or did i somethning wrong.

Thanks in advance

/j

---

### Post by Bachstelze on 2007-05-11
```
export lang=LANG=sv_SE ISO-8859-1
```

Why do you put "lang" twice ? Also, you need to enclose the string in quotes, like this :

```
export LANG="sv_SE.ISO-8859-1"
```

---

### Post by janne5011 on 2007-05-11
ok it says: export command not found

---

### Post by Bachstelze on 2007-05-11
Once again, the magic of Dash !

```
sudo dpkg-reconfigure dash
```

It will ask you if you want to use Dash, say **no**. The reason you have to do this is because of a stupid idea of Ubuntu's developpers to use Dash instead of Bash, "because it's faster", they say. Not only is it not any faster but it also breaks an awful lot of things...

---

### Post by janne5011 on 2007-05-11
true magic now it works.
Big thanks!

---

