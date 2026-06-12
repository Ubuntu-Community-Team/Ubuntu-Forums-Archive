---
title: "Gimp and layers"
date: 2007-10-13
forum: Art &amp; Design
---

### Post by EspAnt on 2007-10-13
Hello, I've started to use gimp one week ago. I'm quite new in these amazing Ubuntu's world. But the thing is that I have problems in viewing layers in my Gimp program. I recieve files made with Macromedia Fireworks (.png) and when I open them with Gimp, all the layers are disappeared.Only the background layer is left. Can someone help me? 
thanz in advance.

---

### Post by leg on 2007-10-13
The png format does not support layers. If you mean that when the image was produced it had layers what will have happened is the image would have been flattened when you saved it as .png.

Natively Gimp uses the .xcf format and saves layer and other info about the image. I have never imported another programs native formats which support layers but I suspect it can be done. Basically the image will need to be saved in a format that saves the layer information. .png . gif .jpeg will not.

---

### Post by exploder on 2007-10-13
I was wondering the very same thing. Thanks for the information!

---

### Post by EspAnt on 2007-10-13
When I open the png file with win-fireworks it has layers.  Anyway, thanks for answering.

---

### Post by leg on 2007-10-13
That program must be maintaining the layer information for the file. See if you can export it in another format to keep the layer info.

---

### Post by Dylnuge on 2007-10-20
> **EspAnt said:**
> When I open the png file with win-fireworks it has layers.  Anyway, thanks for answering.

Fireworks saves additional (proprietary) information into the PNG format so that it can use a universally viewable format while maintaining layers, channels, etc when imported back into Fireworks. A regular PNG that is not created with Fireworks does not have this data, and because it is locked by Adobe, software such as the GIMP does not have access to the Fireworks data.

In reality, the Fireworks PNG is not a regular PNG, however the data in it makes it openable on non-Fireworks computers.

If you need this data on Linux, you have a few options:

1. Convert to .psd (assuming you have Photoshop). I think it is possible in Fireworks, and layers will be exportec.

2. Emulate Fireworks. I think Version 8 works under Wine alright, and I have seen CS3 working fine in VMWare.

---

### Post by AJB2K3 on 2007-10-21
As said before if the layers are needed use the .psd format.

---

