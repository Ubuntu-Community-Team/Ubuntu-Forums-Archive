---
title: "YouTube and Firefox"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-12-16
Hello,

I haven't got sound in YouTube. Could you guide me what the problem is?

Thanks,

---

### Post by pay on 2006-12-16
Try using flash 9 beta 2 ```
wget http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz
tar xvzf FP9_plugin_beta_112006.tar.gz
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/flashplugin-nonfree/ 
```and if that doesn't work try```
sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

```and change ```
FIREFOX_DSP=""
```to```
FIREFOX_DSP="aoss"
```

---

### Post by linux-beginner on 2006-12-16
Thanks, it's solved.
I've got another question. I hoop to get an answer from you. I've asked my question some times in this Forum but nobody has still answered me.
My question: Is it possible to install Dutch language for gnome dictionary?
You make me happy if you give me an answer!
Thanks,

---

### Post by desper on 2006-12-16
AHH, I have the same question. How can we add additional glossaries to gnome dictionary, say, german

---

### Post by pay on 2006-12-16
I am very sorry but since that I don't speak German or Dutch (I thought that they were the same:P shows what I know) I can now answer either of your questions and since majority of this forum speak English, I doubt that you will find an answer on this question. (Sorry to bring your hopes up if you read your answered reply and think that your answer was answered. Hopefully by bumping up this question it will bring more responses as it would help many.) . Good  luck.

---

