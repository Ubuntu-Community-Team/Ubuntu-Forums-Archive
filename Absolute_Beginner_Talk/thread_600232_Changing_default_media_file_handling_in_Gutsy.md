---
title: "Changing default media file handling in Gutsy"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Taxi on 2007-11-02
I just installed Audacious and would like to make that the default application whenever I try to play an MP3 file.  I right clicked and selected "Open With" -> "Open with Other Application...", then chose Audacious from the list.  It said "Open *file* and other files of type 'MP3 audio' with:" which seems like it should change the default application (I think there was a separate "Make Default"-type check box in Feisty).  But what it does is open the file in Audacious that time and make it an entry in the "Open With" menu from then on.  However, the top line on a right click is still "Open with 'Movie Player'" and on double-click it still opens in Totem.  I'd prefer to make VLC my default video player, anyway, plus I don't understand why it's opening an audio file in the movie player when the default audio player is supposed to be Rhythmbox anyway.

So I'd appreciate some help changing my default application in this situation.  Or even better how can I set my default audio and video players for all (or at least most) media formats at once and have it correctly decide to send audio files to Audacious and video files to VLC?  Thanks!

---

### Post by Inxsible on 2007-11-02
> **Taxi said:**
> I just installed Audacious and would like to make that the default application whenever I try to play an MP3 file.  I right clicked and selected "Open With" -> "Open with Other Application...", then chose Audacious from the list.  It said "Open *file* and other files of type 'MP3 audio' with:" which seems like it should change the default application (I think there was a separate "Make Default"-type check box in Feisty).  But what it does is open the file in Audacious that time and make it an entry in the "Open With" menu from then on.  However, the top line on a right click is still "Open with 'Movie Player'" and on double-click it still opens in Totem.  I'd prefer to make VLC my default video player, anyway, plus I don't understand why it's opening an audio file in the movie player when the default audio player is supposed to be Rhythmbox anyway.

So I'd appreciate some help changing my default application in this situation.  Or even better how can I set my default audio and video players for all (or at least most) media formats at once and have it correctly decide to send audio files to Audacious and video files to VLC?  Thanks!
The open with other application is good only for that one time. If you want to change the default app to open a particular kind of file then do this

1) Right click the file of type "whatever". Select Properties.
2) Select the Open With Tab. Select the application that you want to open for that file. If the app you want is not listed you can add it by clicking the Add button and find the app in /usr/bin

---

### Post by Taxi on 2007-11-02
> **Inxsible said:**
> The open with other application is good only for that one time. If you want to change the default app to open a particular kind of file then do this

1) Right click the file of type "whatever". Select Properties.
2) Select the Open With Tab. Select the application that you want to open for that file. If the app you want is not listed you can add it by clicking the Add button and find the app in /usr/bin

Whoops, maybe that IS how I did it in Feisty, though I still feel like it might have just been through the "Open With" -> "Open with Other Application..." dialog.  Anyway, that did the trick, so thank you very much.

Does anyone know if there's a good way to make VLC my default video player and Audacious my default audio player without having to reassociate each file format manually?

---

### Post by Inxsible on 2007-11-02
> **Taxi said:**
> Whoops, maybe that IS how I did it in Feisty, though I still feel like it might have just been through the "Open With" -> "Open with Other Application..." dialog.  Anyway, that did the trick, so thank you very much.

Does anyone know if there's a good way to make VLC my default video player and Audacious my default audio player without having to reassociate each file format manually?
If you do it once for each type of file, that should do it. 

Do you mean you want all audio files like mp3 wav midi etc open with audacious without you having to set it manually ?

I don't think so...or rather I don't know of any.

---

### Post by daengbo on 2007-11-02
System -> Preference -> Preferred Applications in the Multimedia tab.

---

### Post by Taxi on 2007-11-02
> **daengbo said:**
> System -> Preference -> Preferred Applications in the Multimedia tab.

I saw that setting, but didn't mess with it for a couple reasons:

1) Since it only allows one selection, it doesn't seem to allow for separate handling of video and audio files.  This is my main reason, though maybe I could set it to VLC then manually change each audio format I use.

2) It doesn't list VLC, Audacious as options.  I'm sure it could be done by selecting "Custom", but I'm not sure when to use %s or some other % and when it's not necessary, so I would prefer to just select something.   For example, if Firefox is set to make sure it's the default browser, it's not even happy when Firefox is selected in the "Preferred Applications" dialog.  It likes it to be
Custom -> /usr/lib/firefox/firefox "%s"
for some reason that I don't understand.

---

