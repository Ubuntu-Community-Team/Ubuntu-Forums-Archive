---
title: "where is adesklets:D"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by soutSA on 2006-10-19
This might be a silly question, but I have installed adesklets:

#sudo apt-get install adesklets

but I can not seem to find it. It is installed and can find all files related to it, but I cant seem to find it.

If I run adesklets, nothing happens. How do I access it?

Thanks in advance

---

### Post by raul_ on 2006-10-19
I'll assume you're using gnome. First of all u have to register the desklets. After that run
```

adesklets --nautilus

```

and something should happen...i think :rolleyes:

---

### Post by metalsam on 2006-11-02
how do you register them ?

I installed using hte adesklets -i  and it said it insatlled the desklets i wanted... but when i do adesklets --kde nothing happens :s

---

### Post by raul_ on 2006-11-02
enter the path of the desklet and type "./<name>.py"

---

### Post by patrick295767 on 2006-11-05
[http://doc.gwos.org/index.php/Adesklets](http://doc.gwos.org/index.php/Adesklets)

1/ apt-get install adesklets


2/ wget [http://dl.sourceforge.net/sourceforge/adesklets/weatherforecast-0.2.0.tar.bz2](http://dl.sourceforge.net/sourceforge/adesklets/weatherforecast-0.2.0.tar.bz2).


3/ tar -xvjf weatherforecast-0.2.0.tar.bz2 
mv weatherforecast-0.2.0 ~

4/ cd  weatherforecast-0.2.0

5/ 

6/ gedit nano config.txt

7/ place in this config.txt
> id0 = {'background_image': '',
'delay': 300,
'font_conditions': 'Vera',
'font_conditions_color': '000000',
'font_conditions_size': 12,
'font_location': 'Vera',
'font_location_color': '000000',
'font_location_size': 16,
'font_temperature': 'Vera',
'font_temperature_color': '000000',
'font_temperature_size': 12,
'full_background': False,
'icon_size': 128,
'location': 'MBXX0001',
'location_alternate_text': None,
'metric': True,
'min_height': 130,
'min_width': 260,
'temperature_symbol': 'deg.C',
'text_icon_overlapping': 10,
'text_padding': 5}

7.5/
cd weatherforecast-0.2.0 
./weatherforecast.py
say r 
to register

7.6/ adesklets -i 
( it can sometimes be not fully workign great 'error tk')
 
( you need : [COLOR="Red"]apt-get install python2.4-tk[/COLOR]
and also TK )
 

8/go there
[http://www.weather.com/outlook/travel/businesstraveler/local/AUXX0016?from=recentsearch](http://www.weather.com/outlook/travel/businesstraveler/local/AUXX0016?from=recentsearch)
enter ur city
in the address bar of firefox : get the city label nuber and replace MBXX0001

9/  killall -e adesklets

10/ adesklets &

Enjoy now the Weather with Adesklets on your desktop ! :-D ;) 

Patrick

---

### Post by metalsam on 2006-11-06
> **raul_ said:**
> enter the path of the desklet and type "./<name>.py"

I did that, then executed adesklets like the registration said to, but noting happened.

I tried ps -A and it didnt show up there....

---

### Post by raul_ on 2006-11-06
first u need to test it. If u see a flicker in the top left corner then do it again but this time register it. after that run "adesklets --nautilus" and it should work. if it doesn't work probably the test will reveal the error

---

### Post by patrick295767 on 2006-11-06
by the way, there is not much adesklets on the sourceforge... 
Is there everthg existing .?:confused: 

gdesklets has more maybe...

Greetings

===
when u run the py extension file; you register it; which means you write into the $HOME/.adesklet file

---

### Post by metalsam on 2006-11-12
I installed systemmonitor and its dependancies, but when i test the desklet i get this message:
```

Traceback (most recent call last):
  File "./SystemMonitor.py", line 43, in ?
    import statgrab
  File "/usr/lib/python2.4/site-packages/statgrab.py", line 23, in ?
    import _statgrab
ImportError: libstatgrab.so.6: cannot open shared object file: No such file or directory

```

However, a whereis shows it to be on my system:
```

sam@sam-kubuntu:~/.desklets/SystemMonitor-0.1.3$ whereis libstatgrab.so.6
libstatgrab.so: /usr/local/lib/libstatgrab.so.6 /usr/local/lib/libstatgrab.so

```

Anyone know how to fix this ? Thanks.

---

### Post by raul_ on 2006-11-12
maybe u have to create a link. Anyway, i think u should check the adesklets forum. pretty much every problem is solved there. here's the link

[http://adesklets.sourceforge.net/forum]("http://adesklets.sourceforge.net/forum")

---

