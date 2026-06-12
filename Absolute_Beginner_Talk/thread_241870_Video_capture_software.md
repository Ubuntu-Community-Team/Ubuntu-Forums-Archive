---
title: "Video capture software"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Yusayoh on 2006-08-22
I have a USB Digital Video Camera (Sony) and when I connect it to my computer, I want to be able to capture video from it, save it to my hard drive and edit it (it doesn't need to be only one program). Can anyone help me?

---

### Post by Houman on 2006-08-23
Hi there;
there are a lot of programs that let you play around with your webcam (save pics, vids...) but first you need the drivers for your webcam. Im not sure if youre webcam is recognized by ubuntu or you have to do extra work, here is a great link for getting started with webcams: [WebCam HowTo]("http://www.linux.com/howtos/Webcam-HOWTO/hardware.shtml")

also you can check if youre webcam is working by getting one of those webcam programs, my favourite is gqcam (its simple and does the job). But there are also more complicated ones like xawtv (both available in teh repositories). By the way you can see a list of applications you can use with youre webcam in the link above.

good luck

---

### Post by k94382 on 2006-08-23
i dont think it's a webcam. sounds like a real video camera to me.

---

### Post by Marsolin on 2006-08-23
[Kino]("http://linuxappfinder.com/package/kino") is a good program for importing video from a camera and editing it as well. There was a write-up on it in the August issue of [Tux Magazine]("http://www.tuxmagazine.com").

---

### Post by Houman on 2006-08-23
oh boy you are right, 
I have spent way too much time playing with my webcam that now i think every post is webcam related, no wonder i couldnt find any drivers for a "sony" webcam when i was googling around for him, jeez ](*,) 

I kinda got the wrong idea when he said "capture" i thought he means grab a frame from it in real-time like a webcam, rather than download from;

oh well


Houman

---

### Post by Yusayoh on 2006-08-23
Thanks for the replies.
It's a sony Handycam. Yes, a real digital video camera (not a webcam). I've tried Kino but it doesn't pick it up and Ubuntu doesn't pick it up either. Any suggestions?

---

### Post by Marsolin on 2006-08-23
You could also try [PiTiVi]("http://linuxappfinder.com/package/pitivi").

---

### Post by Yusayoh on 2006-08-23
That's not working either :(

---

### Post by professor_chaos on 2006-08-23
I use dvgrab to capture from my dv sony cam via firewire.

```
sudo apt-get install dvgrab
man dvgrab
```

ex.
```
dvgrab -i --autosplit --timestamp video
```

very flexable. No need for gui's here. Good luck.

---

### Post by Yusayoh on 2006-08-23
Is it possible with USB?

---

### Post by deadgobby on 2006-08-23
> **Yusayoh said:**
> I have a USB Digital Video Camera (Sony) and when I connect it to my computer, I want to be able to capture video from it, save it to my hard drive and edit it (it doesn't need to be only one program). Can anyone help me?

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaDigitalCameras?highlight=%28Camera%29](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaDigitalCameras?highlight=%28Camera%29)

---

