---
title: "Problems installing packages in TexLive and Edgy"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by AiRAVATA on 2006-11-18
Hello guys. I am new to Ubuntu and I am working with Edgy Eft.

I did a clean install of TexLive and Kile with no probs. Im trying to install bbold fonts from the live CD with the following code:

```
sh install-pkg.sh --package=bbold
```

only to get the following errors in every directory that TexLive is trying to create:

```
checkdir error:  cannot create texmf-dist/doc/latex/bbold
                 unable to process texmf-dist/doc/latex/bbold/INSTALL.
checkdir error:  cannot create texmf-dist/doc/latex/bbold
                 unable to process texmf-dist/doc/latex/bbold/README.
checkdir error:  cannot create texmf-dist/source/latex/bbold
                 unable to process texmf-dist/source/latex/bbold/bbold.dtx.
checkdir error:  cannot create texmf-dist/source/latex/bbold
...

```

I have also tried to install it manually, creating the dirs myself and doing a texhash, but kile cannot see the metric files...

What am I doing wrong?

Thx in advance and sorry for bad english.

---

### Post by AiRAVATA on 2006-11-18
Well, I was able to install the package as root, but I sure would be happier if I did not have to do that.

Does anyone knows a better way?

---

