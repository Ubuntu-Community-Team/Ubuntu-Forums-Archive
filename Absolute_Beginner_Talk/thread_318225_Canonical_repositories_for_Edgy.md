---
title: "Canonical repositories for Edgy?"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-12-13
Does anyone know how the line for the canonical repositories should look like?

This is the one for Dapper:
```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

So how about edgy?

Thanks

---

### Post by K.Mandla on 2006-12-13
I believe it should be 

```
deb http://archive.canonical.com/ubuntu **edgy**-commercial main
```
but I'm not 100 percent sure. I have them tacked on to my repository list and I don't get errors on *update*s, so I guess they should work. I can't think of anything I've installed out of the commercial repositories, though.

---

### Post by Jucato on 2006-12-13
The edgy-commercial repository does exist, but it is also empty. I don't think they have plans on making Opera and Real Player available through that repository. I had to resort to a 3rd party repository for Opera. I don't mind that, though, since the packager and owner of the repository is my friend. :P

---

