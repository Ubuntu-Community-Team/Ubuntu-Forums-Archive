---
title: "[SOLVED] Firefox Font Problem"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-02-03
Hello!
I was a hardy user. But I installed gutsy. Both of them have firefox1, but just in gutsy, I have some problems with some Iranian web pages. I know it might not be easy for who doesn't know Farsi to judge these pictures, but the first is an incorrect page and the second is a correct one. What should I do?
Thanks.

---

### Post by Cato2 on 2008-02-03
Hi, you really need to explain what's incorrect - I can't see any incorrect fonts or character encodings there.

---

### Post by Hoom@n on 2008-02-05
In the farsi forums they told me to:
```
sudo apt-get install ttf-farsiweb xfonts-intl-arabic xfonts-intl-european xfonts-intl-phonetic
```
And then:
```
wget -c http://heanet.dl.sourceforge.net/sourceforge/fpf/fpf.zip
wget -c http://hezardastan.sourceforge.net/persianfonts/tahoma.tar.gz
wget -c http://hezardastan.sourceforge.net/persianfonts/bfonts.tar.gz
sudo mkdir /usr/share/fonts/truetype/ttf-persian-fonts
sudo unzip fpf.zip -d /usr/share/fonts/truetype/ttf-persian-fonts
sudo tar zxvf tahoma.tar.gz -C /usr/share/fonts/truetype/ttf-persian-fonts
sudo tar zxvf bfonts.tar.gz -C /usr/share/fonts/truetype/ttf-persian-fonts
```
And finaly:
```
sudo fc-cache -f -v
```
1-Do you think it's safe?
2-Will it slow down my computer?
Thanks.

---

### Post by Hoom@n on 2008-02-05
It worked and everything is ok!

---

