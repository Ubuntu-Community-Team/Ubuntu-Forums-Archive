---
title: "High definition quality?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by haxer on 2008-02-04
Hi i have a question about high definition "hd" in linux. Is it working? Ive hade it in windows with cccp codecs but it is working in linux yet?:)

---

### Post by PeterJS on 2008-02-04
That's kind of a vauge question. Which specific codecs and resolutions are you wondering about?

---

### Post by haxer on 2008-02-04
Ok I try to be a bit more specific .... hmm.. is  highdefinition movies able to play in ubuntu 7.10 like in windows. Or do i need some special codecs to play hd movies or tv broadcasting? you know the 720dpi or 1080dpi.

---

### Post by PeterJS on 2008-02-04
Looks like the current mplayer can play HD content. Decryption on HD content doesn't look nearly as elegant as for standard DVDs, so it's going to take a bit (~30Gb) of disk space.

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

Looks like the same ffmpeg codecs used on windows are used by mplayer so it should be able to handle anything. Also VLC prides themselves on playing anything and everything, so you might give that a go as well.

---

### Post by emarkd on 2008-02-04
There are lots of codecs for "storing" video and they're independent of the resolution.  I've used my Linux boxen for working with plenty of "HD"quality video that is encoded as MPEG and wrapped in AVI or MKV containers, but know that some of these codecs are proprietary and are not included in Ubuntu by default.  Installing them is easy, though.

---

### Post by haxer on 2008-02-04
Ok uhm... any way for you to tell me how or where to download them? I mean the codecs. I usually get straight dvd .vob format with x264 and that lookes great for watching movies but i need some codecs becuse in windows i had to. So where to get them?

---

### Post by emarkd on 2008-02-04
Stick with Synaptic for downloading software unless you've got a real good reason no to.  Lots of them are in ubuntu-restricted-extras, or you can add [Medibuntu]("http://www.medibuntu.org/") to your apt setup and install w32codecs.

---

### Post by haxer on 2008-02-05
And then it will work? Just like that? W32 codecs means that its windows codecs .. .but even windows doesnt have it from scratch...

---

### Post by billgoldberg on 2008-02-05
I know that vlc plays 720 (and whatever letter comes behind it) and 1080 .avi's because i'v done it.

---

### Post by emarkd on 2008-02-05
Well, it depends on the codecs you want to use.  [Here's]("http://http://debian-multimedia.org/dists/stable/main/binary-i386/package/w32codecs.php") what's included in w32codecs.  VOB, by the way, is just a wrapper around MPEG2 video.  They'll play with no problems.

---

### Post by haxer on 2008-02-05
Server not found

      

      
      
      

      
        
        

          

Firefox can't find the server at http.

        


        
        


    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.



I will try it today see if it works hope i notice it again :)

---

