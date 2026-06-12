---
title: "Anyone know Lilypond? (need help...)"
date: 2005-12-29
forum: Art &amp; Design
---

### Post by Minyaliel on 2005-12-29
Right, I'm trying this program right now, and can't really get anything done. :P I've got to have this notation thing for school when it starts again... I can't get it to print out the music. I even tried copying an input for a score off [www.lilypond.org](www.lilypond.org), and I still couldn't make it work. Screenshot included... any help would be gratefully accepted, this issue is giving me a major headache:???:

---

### Post by theCore on 2005-12-30
I don't much about about lilypond except that it is a fantastic program for generating beautiful score.
I suggest that you install a newer version of lilypond 2.6. Here an original way to do it with the terminal:
```

sudo aptitude remove lilypond     # remove the older installation
wget http://ftp.ubuntulinux.org/ubuntu/pool/universe/l/lilypond/lilypond{_2.6.3-9~breezy1_i386.deb,-data_2.6.3-9~breezy1_all.deb,-doc_2.6.3-9~breezy1_all.deb}   # get the newer version from ubuntu universe reporistory
sudo aptitude install guile-1.6   # lilypond depend on it
sudo dpkg -i lilypond*.deb        # install lilypond, enjoy!

```

then test your installation:
```

wget http://lilypond.org/doc/v2.6/input/mutopia/E.Satie/petite-ouverture-a-danser.ly.txt
mv petite-ouverture-a-danser.ly.txt petite-ouverture-a-danser.ly
lilypond petite-*.ly

```

It's worked on my system, so this will probably work for you too :)

P.S.: This is not a support channel. So please, try to avoid posting support request  here.

---

### Post by Minyaliel on 2005-12-31
Hey, thanks, and sorry for my newbieishness ;) Happy new year, btw :) *is watching fireworks booming over neightbour's roof top*

---

