---
title: "Kill me now plz!!!"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by Akira_Oni on 2006-08-02
Just for history's sake, my woe's were originally documented [here.]("http://ubuntuforums.org/showpost.php?p=1313097&postcount=661")

Problem is when I say n00b, I dont just mean Ubuntu Newbie... I seriously mean I'm completely new to Linux. I've had minimal experiance with unix, but honestly I'm not very experianced there either.

I've been trying REEEEEALLY hard to understand using command line. I'm even finding that, on some level, I enjoy it... until I realize I dont know how to open applications... or do anything useful other than "cd" my way around. I also find that I'm having severe issues installing programs I need.

Here are a few examples:

---

As with the previously mentioned suggestion about modifying my tablet, in trying to add automatix to my installation database, I find I cant save the files because they are listed as belonging to me. However, unless I'm in terminal I cant sudo the app... and in terminal I have no clue what I'm doig.

---

I'm trying to install [Nautilus]("http://www.gnome.org/projects/nautilus/"), to use with [Audio-Convert]("http://linux.softpedia.com/get/Multimedia/Audio/Audio-Convert-3104.shtml") (I think that's the right program). I try to ./configure the file ... I get this error:

```
configure: error: Library requirements (
        esound                  >= 0.2.27
        bonobo-activation-2.0   >= 2.1.0
        eel-2.0                 >= 2.12.0
        glib-2.0                >= 2.6.0
        gnome-desktop-2.0       >= 2.9.91
        gnome-vfs-2.0           >= 2.11.1
        ORBit-2.0               >= 2.4.0
        pango                   >= 1.1.2
        gtk+-2.0                >= 2.6.0
        libart-2.0              >= 2.3.10
        libbonobo-2.0           >= 2.1.0
        libgnome-2.0            >= 2.1.1
        libgnomeui-2.0          >= 2.6.0
        librsvg-2.0             >= 2.0.1
        libxml-2.0              >= 2.4.7

```

I cant even find half this crap. I did go dl libxml-2.0 myself... came in a nicely packaged gz format THAT I CANT OPEN!!! I try to apt-get... yeah, not gonna happen.

---

Totem Media Player. Nuff said

---

Can someone please refer me to a vector based program that's better than Inkscape? Perhaps something that I wont want to kill my computer after using. I'm sure this one has been answered before, but I thought to add it in.

---

I am finding Linux to be comperable to, if not better than, Windows. However, I wanna do more than just chat/check e-mails... and it's really not agreeing with me. Can someone help me so that issues like this dont ruin what could be a generally good experiance for me?

---

### Post by croak77 on 2006-08-02
If you are using Ubuntu (GNOME) Nautilus is already installed. If not, open a terminal and type:

```
 sudo aptitude install nautilus 
```

To install Audio-Convert type:

```
sudo aptitude install nautilus-script-audio-convert 
```

You will need to have universe enabled in your sources.list. For help go here.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Almost forgot to mention, after anytime you change your sources.list you need to run;

```
 sudo aptitude update 
```

For totem, if you are using gstreamer you will need the proper gstreamer plugins if you are using totem-xine you will need the w32codecs and libxine-extra. I suggest installing totem-gstreamer as well as either gxine or mplayer.  Follow directions here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Inkscape is most likely the best vector program for linux. There is a KDE program called karbon but I don't use these so I have no idea which is better.

---

### Post by T700 on 2006-08-02
I'm sorry that you're having these problems.  Let me make a suggestion that help.  It is *much* better to make descriptive titles for your posts.  More people will look at a thread with a title that tells you the basics of the trouble than will check out "Kill me now plz!!!", "hELP!!!", or the like.  

You mght also consider breaking up seperate problems into seperate posts.

Good luck,
Paul

---

### Post by Dr. Nick on 2006-08-02
Alot of stuff if icluded in the respositores already and does not require source building. On your configure error you could look up those names in synapic and install the -lib versions. But as mentioned audi convert is installable without compiling

Look her for some good starting info

[https://help.ubuntu.com/community/CommonQuestions#head-ff74a24f24dd12670bbc0130cc84460c03dc5dae](https://help.ubuntu.com/community/CommonQuestions#head-ff74a24f24dd12670bbc0130cc84460c03dc5dae)

Plus some of the links below in my sig may be helpful

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by croak77 on 2006-08-03
Double Post. Sorry.

---

### Post by croak77 on 2006-08-03
For your tablet I'd go to this thread;

[http://www.ubuntuforums.org/showthread.php?t=25151&highlight=graphire](http://www.ubuntuforums.org/showthread.php?t=25151&highlight=graphire)

Try following what other people did, If you run into problems ask for help in that thread since it's people who have tablets like yours.

---

