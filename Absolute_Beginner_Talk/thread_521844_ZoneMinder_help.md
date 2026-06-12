---
title: "ZoneMinder help"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Panganat on 2007-08-09
tried the tutorials to get it to go but had no luck to get to start on boot.  is there a coomand to start it from the terminal? :confused:

---

### Post by rampage_1973 on 2007-11-14
sudo /etc/init.d/zoneminder start

try that it should work. (does on mine anyway )

---

### Post by kris_a on 2008-01-23
Hello,

not sure if you got there in the end, but I just managed to get ZoneMinder working and this might help someone else... this is what I had to do:

1) Added zoneminder package using Synaptic
2) Copy apache config file to correct directory (ln -s did not work, too many links for apache!):

```
sudo cp /etc/zm/apache.conf /etc/apache2/conf.d/
```

3) Restart apache

```
sudo /etc/init.d/apache2 restart
```

Try it now, go to [http://127.0.0.1/zm]("http://127.0.0.1/zm") it should show the main page.
If when you have added a video source the name (i.e. /dev/video0) stays red in the list then you might need to do the following to grant ZoneMinder access to the video devices:

```
sudo usermod -a -G video www-data
```

After this mine works fine including all the recording/motion detecting goodness.  Now, I don't know if doing any of this causes any security problems so ask somebody who knows if you have a public server, I just use this locally.

Enjoy :)
Kris.

EDIT: Forgot to mention I am running Ubuntu Gutsy

---

### Post by theorganloft on 2008-02-17
> **kris_a said:**
> Hello,

not sure if you got there in the end, but I just managed to get ZoneMinder working and this might help someone else... this is what I had to do:

1) Added zoneminder package using Synaptic
2) Copy apache config file to correct directory (ln -s did not work, too many links for apache!):

```
sudo cp /etc/zm/apache.conf /etc/apache2/conf.d/
```

3) Restart apache

```
sudo /etc/init.d/apache2 restart
```

Try it now, go to [http://127.0.0.1/zm]("http://127.0.0.1/zm") it should show the main page.
If when you have added a video source the name (i.e. /dev/video0) stays red in the list then you might need to do the following to grant ZoneMinder access to the video devices:

```
sudo usermod -a -G video www-data
```

After this mine works fine including all the recording/motion detecting goodness.  Now, I don't know if doing any of this causes any security problems so ask somebody who knows if you have a public server, I just use this locally.

Enjoy :)
Kris.

EDIT: Forgot to mention I am running Ubuntu Gutsy

THANKS FOR THIS POST.  I was frustrated until you saved the day.  Thanks again!

---

