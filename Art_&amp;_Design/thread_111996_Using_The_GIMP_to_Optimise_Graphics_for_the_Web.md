---
title: "Using The GIMP to Optimise Graphics for the Web?"
date: 2006-01-03
forum: Art &amp; Design
---

### Post by Ted_Smith on 2006-01-03
Anyone know how to replicate the 'Optimise fo Web' feature seen in Photoshop using The GIMP? I do a lot of web production stuff, and with Photoshop I just used to go 'File --> Optimize for Web', and it would show me 4 pictures starting from not optimised to fully optimised, with details of the reduction in memory usage vs loss of quality. I can't figure out how to do the same thing with The GIMP?

Thanks

Ted

---

### Post by stuporglue on 2006-01-03
Do you know what the optimize for web did? Are you just trying to get the smallest file size with the best atributes you can?

The things I can think of are pretty easy to do manually. I don't know of an automated tool that does them in the Gimp though. 

1) Change the image to indexed. Image menu-->Mode--> Indexed   adjust to taste

2) Change the compression level in your PNG while not saving resolution, creatino time, or comment. (file-->save as--> choose png, use check boxes.

3) Use the advanced options when saving as a jpg. Turn down the quality to the minimal acceptable (show preview in image window to watch it happen), and manually tweak the other options.

---

### Post by zami on 2006-07-26
Hello all!

(Sorry to revive an old thread, but I had almost the exact same question as the original poster and thought I'd save the next searcher a smidge of time.)

I'm looking for a replacement for an old favorite program of mine, called Image Lab.

It was VERY simple... no image editing, just compression of .jpg and .bmp files. 

You could set the image size, resolution, format (a few other compression methods I never understood), and then simply apply it, open your next image, apply it again, open your next image... 

It made "shrinking" multiple images VERY fast an easy.  And as you saved, it would also list the size of the file and the approximate time it would take to up/download over various connection speeds.

Yes, it was probably my favorite program!

So now, I am looking for a Linux compatable replacement.

OR, would it be possible for a GIMP newbie like myself to make a script to automate some of this?  

I do understand how to 'optimize' images in GIMP but so far it seems a four part SLOW and tedious process. 

Any advice will be much appreciated!

-zami

---

### Post by gavinhughes86 on 2010-01-04
Well this might be a bit late but their is a plugin for gimp that imho is great for optimising images for web, 
"save for web"

its available here
[http://registry.gimp.org/node/33](http://registry.gimp.org/node/33)

It has one requirement the 
 libgimp2.0-dev

installed by 
```
sudo apt-get install libgimp2.0-dev
```their is a readme that comes with the file its fairly straight forward

---

### Post by Exodist on 2010-01-04
4 year old thread. I dont think they are still waiting on this information. /necropolis

---

