---
title: "Mona font in firefox and Opera"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by DianWei on 2006-08-02
Sorry to bother you guys, but I am having difficulty getting Shift_jis art working in Linux... for some reason rows are shifted in ways they shouldn't be...

For example, take a look at the snapshot...
[[IMG]http://img58.imageshack.us/img58/8433/screenshot1228896322chbbsfirefoxzf7.th.png[/IMG]](http://img58.imageshack.us/my.php?image=screenshot1228896322chbbsfirefoxzf7.png)


One can see how the picture should line up, and how it is not lining up, anyone know what I am doing wrong?

---

### Post by Agent86 on 2006-10-07
I am having the same problem as the OP. I installed the xfonts-mona package from Synaptic and the Ubuntu repositories. I tried to use Fonts & Colors tool in Firefox to activate mona as the preferred monospaced font, but no font with "mona" in the name appears in the available fonts list.

Is there another package I have to install, or to configure x11 or Firefox in some way to activate the mona font?

There is also a more recent .deb for mona font available, should I try unistalling the Synaptic package and installing the .deb?

---

### Post by Agent86 on 2006-10-10
[http://wakaba.c3.cx/sup/kareha.pl/1125721701/](http://wakaba.c3.cx/sup/kareha.pl/1125721701/) for the answer.

If you installed the xfonts-mona package available in the repos, you probably want to uninstall it first.

Now, either install the .deb available at
[http://utyuuzin.net/debian/lab/ttf-mona_2.90-0.1_all.deb]("http://utyuuzin.net/debian/lab/ttf-mona_2.90-0.1_all.deb")

Or extract mona.ttf from monafont-ttf-2.90.zip at
[http://sourceforge.net/project/showfiles.php?group_id=55807]("http://sourceforge.net/project/showfiles.php?group_id=55807")
and then
```
sudo mkdir /usr/share/fonts/truetype/mona
sudo cp mona.ttf /usr/share/fonts/truetype/mona/

```

Whether you use the .deb or the .ttf, do a
```
sudo fc-cache -v
```
afterwards. Now mona should show up in the list of fonts available to Firefox. I tried this on separate PCs; both methods worked for me.

---

