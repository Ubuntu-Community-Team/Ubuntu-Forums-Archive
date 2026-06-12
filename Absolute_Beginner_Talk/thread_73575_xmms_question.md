---
title: "xmms question"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by crackity on 2005-10-09
i've followed the ubuntuguide how to set up xmms. Everything is working well but i have a question on how you remove xmms to be your default mp3 player? Im talking about removing those commands:

Associate XMMS to play MP3/M3U/WAV files
```

sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo cp /usr/share/applications/defaults.list /tmp/defaults.list_tmp
sudo sed -e 's/audio\/mpeg=.*/audio\/mpeg=XMMS.desktop/g' /tmp/defaults.list_tmp > /tmp/defaults.mp3
sudo sed -e 's/audio\/x-mpegurl=.*/audio\/x-mpegurl=XMMS.desktop/g' /tmp/defaults.mp3 > /tmp/defaults.m3u
sudo sed -e 's/audio\/x-wav=.*/audio\/x-wav=XMMS.desktop/g' /tmp/defaults.m3u > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list
sudo rm -f /tmp/defaults.*
```

Thx

---

### Post by Kyral on 2005-10-09
```
sudo mv /usr/share/applications/defaults.list_backup /usr/share/applications/defaults.list
```

---

### Post by crackity on 2005-10-09
thx for the quick answer

---

