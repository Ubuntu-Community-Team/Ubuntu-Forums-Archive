---
title: "CYMK in GIMP?"
date: 2008-08-05
forum: Art &amp; Design
---

### Post by Giant Speck on 2008-08-05
Hello,

I'm trying to make a poster for a contest, but the entry rules state that the color format of the artwork must be CYMK.

I can't figure out how to do that on GIMP.  Is there even a way to do it?

Thanks
Jesse

---

### Post by hessiess on 2008-08-06
gimp cannot do cymk

---

### Post by Neon Lights on 2008-08-06
> **hessiess said:**
> gimp cannot do cymk
*yet.

it is planned, but at the current time, it's not functional. ): Sorry.

---

### Post by AJB2K3 on 2008-08-07
Try this - [http://cue.yellowmagic.info/softwares/separate.html]("http://cue.yellowmagic.info/softwares/separate.html")

---

### Post by noteviljoe on 2009-06-17
I have been messing around with this and found that you can get the gimp plug in by adding gimp-plugin-registry and ICC-profiles using synaptic

---

### Post by chips24 on 2009-06-17
i thought the new version of gimp could support CMY. what do i know...

---

### Post by jedimasterk on 2009-06-19
The Gimp developers for some lame brain reason, don't plan on putting CMYK support in Gimp. It's again'st their philosophy. They want to try and get the same results in other ways. Hence why Gimp will never be used for professional printing. Krita and digiKam does support CMYK. Kind of like ogg format being the prefered format for open source, but the required format being mp3. And someone telling you that mp3 support will never be included, because ogg is just as good.

---

### Post by Neon Lights on 2009-06-19
> **jedimasterk said:**
> The Gimp developers for some lame brain reason, don't plan on putting CMYK support in Gimp. It's again'st their philosophy. They want to try and get the same results in other ways. Hence why Gimp will never be used for professional printing. Krita and digiKam does support CMYK. Kind of like ogg format being the prefered format for open source, but the required format being mp3. And someone telling you that mp3 support will never be included, because ogg is just as good.
Where on earth did you hear that?

---

### Post by jedimasterk on 2009-06-19
> **Neon Lights said:**
> Where on earth did you hear that?

At Libre Graphics 2009. The Gimp developer talked about the UI, than talked about CMYK. He said that it was not about CMYK, but plates. Getting Gimp to work with high end printers. Also has a nice slide with CMYK and a big line throught it. youtube Libre Gpaphics 2009. Check out the link below.

[http://www.mmiworks.net/eng/publications/blog.html](http://www.mmiworks.net/eng/publications/blog.html)

---

### Post by azangru on 2009-06-19
> At Libre Graphics 2009. The Gimp developer talked about the UI, than talked about CMYK.

Yeah, and here is the recording of his talk and slides (the first 20 minutes or so of his talk are about CMYK)

[http://river-valley.tv/media/conferences/lgm2009/0202-Peter_Sikking/](http://river-valley.tv/media/conferences/lgm2009/0202-Peter_Sikking/)

Frankly, I am confused. One minute he talks about CMYK support, next thing you know he says it's not CMYK support, then he says we'll get the option of exporting CMYK files, then he crosses CMYK out. I understand his idea of doing all the major editing in the RGB mode and then just doing some touch-up before exporting the file to some printer-friendly version, but what's all this fuss about "plates"? And will the exported file be in CMYK as the printer requires? Does anybody understand this? Can anybody explain?

---

### Post by Mohamedzv2 on 2009-06-19
Are you serious? I read before that one of the reasons they switched to GEGL is because it would make it easier to add CMYK and more than 8 bit.

---

### Post by amac777 on 2009-06-20
If you are running Jaunty, there is a gimp plugin for doing CYMK called Separate in the reposistories already. You need to install the following two packages to get the plugins and the adobe color profiles:

```
sudo apt-get install gimp-plugin-registry
sudo apt-get install icc-profiles
```

Then you can convert your final image (make it all one layer first) to CYMK by going to Image -> Separate -> Separate in the gimp menus.

PS: when I tested this, it works even though it will complain about the color profiles being incorrect. Just ignore the error warnings and continue and it should work fine. The error warnings might be fixed already. This bug report has more info about that:

[https://bugs.launchpad.net/ubuntu/+source/gimp-plugin-registry/+bug/353084](https://bugs.launchpad.net/ubuntu/+source/gimp-plugin-registry/+bug/353084)

---

### Post by Giant Speck on 2009-06-20
Damn.  I forgot I made this thread.  It's almost a year old, too!

---

### Post by AJB2K3 on 2009-06-20
For the sake of simplicity I'm going to say that Plates and CMYK are the same thing ( I know there not but this is for simplicity sake)

A professional printer uses for printers for printing things, each will only print 1 colour (yes I know some can print all the colors)
Cyan,
Magenta,
Yellow,
Black.

A printer will make a plate for each colour and the flyer will get pressed with each plate which is supposed to make clearer crisper prints.

For a printer to do this it needs the separate colours profiles generated by a CMYK profile.

As long as the gimp crew can generate this information it doesn't matter weter there use CMYK system or another system.

---

### Post by cubeist on 2009-06-20
> **AJB2K3 said:**
> 
... A professional printer uses for printers for printing things...


great quote! LOL

I have had ok results from using the Colors/Components/Decompose plugin, then decompose to CMYK and uncheck save to layers.  This will create four new images (a C,Y,M, and K) which you can save individually and then send to your printers.  Essentially you are providing them masks for each color plate.

However, most printers don't really care if you send them an RGB these days because they will CMYK it on the fly.

---

