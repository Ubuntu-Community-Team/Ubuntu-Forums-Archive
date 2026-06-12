---
title: "KDE applications crashing on Gnome desktop"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by RaiSuli on 2006-01-19
Hi,

there are only two KDE applications I use often on my Gnome desktop. One his k3b, the other is the newsreader klibido. Both are giving me problems. K3b hangs up while "scanning for cd devices", am getting no other error messages. Klibido is a bit more forthcoming when it crashes on start. The terminal gives me this:

DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-claudia"
Link points to "/tmp/kde-claudia"
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: '/usr/share/applications/themus-theme-applier.desktop' specifies undefined mimetype/servicetype 'application/x-gnome-theme-installed'
kbuildsycoca: WARNING: '/usr/share/applications/ooo2-math.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.math'
kbuildsycoca: WARNING: '/usr/share/applications/nautilus-folder-handler.desktop' specifies undefined mimetype/servicetype 'x-directory/gnome-default-handler'
kbuildsycoca: WARNING: '/usr/share/applications/nautilus-folder-handler.desktop' specifies undefined mimetype/servicetype 'x-directory/normal'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'application/x-extension-mp4'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'application/x-extension-m4a'

And so on...

Klibido itself gives me the following error message:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)

I installed both programs using apt-get.

Can anyone help?

---

### Post by RaiSuli on 2006-01-19
Anyone please? Found nothing on the boards that seems to relate to this problem.

---

### Post by bscbrit on 2006-01-19
I can only suggest that you install kde-desktop to provide the support structure for the 2 KDE programs that you are trying to run.  I'm not certain about this advice as a cure, but I do not see how it can cause any problems. :p

---

### Post by Sef on 2006-01-19
have you tried removing them and then re-installing them?

1) sudo apt-get remove --purge k3b klibido

2) sudo apt-get install k3b klibido

---

### Post by RaiSuli on 2006-01-19
Yes, I've been thinking about that too. Will try it in the morning. Thanks!

@Sef: Tried that several times, always with the same result.

---

### Post by patrick295767 on 2006-01-21
I am using fvwm with the kicker bar
it's rather like kde and much faster
  
Did you try under fvwm ?
mayeb that can hel p
  
Greetz

---

### Post by RaiSuli on 2006-01-21
I've installed Fluxbox this morning, and Klibido and K3b seem to like this enviroment much more. :)
I'll probably stick with it or play around with some other desktops.

---

