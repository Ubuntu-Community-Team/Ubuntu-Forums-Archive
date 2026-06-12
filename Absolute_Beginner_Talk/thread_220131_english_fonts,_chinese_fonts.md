---
title: "english fonts, chinese fonts"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by danbuntu on 2006-07-21
i am using english locale, and installed wqy chinese fonts suits.
the chinese looks fine now.

following is my /etc/language-selector.conf

<fontconfig>

<alias>

<family>serif</family>

<prefer>

<family>Bitstream Vera Serif</family>
<family>WenQuanYi Bitmap Song</family>
<family>DejaVu Serif</family>
<family>AR PL ShanHeiSun Uni</family>
<family>AR PL ZenKai Uni</family>

</prefer>

</alias>

<alias>

<family>sans-serif</family>

<prefer>

<family>Bitstream Vera Sans</family>
<family>WenQuanYi Bitmap Song</family>
<family>DejaVu Sans</family>
<family>AR PL ShanHeiSun Uni</family>
<family>AR PL ZenKai Uni</family>

</prefer>

</alias>


<alias>

<family>monospace</family>

<prefer>

<family>Bitstream Vera Sans Mono</family>
<family>WenQuanYi Bitmap Song</family>
<family>DejaVu Sans Mono</family>
<family>AR PL ShanHeiSun Uni</family>
<family>AR PL ZenKai Uni</family>

</prefer>

</alias>


<match target="font" >

<test name="family" compare="contains" >

<string>Song</string>

<string>Sun</string>

<string>Kai</string>

<string>Ming</string>
</test>
<test name="weight" compare="less_eq">
<int>100</int>
</test>

<test compare="more_eq" target="pattern" name="weight" >

<int>180</int>

</test>

<edit mode="assign" name="embolden" >

<bool>true</bool>

</edit>

</match>

<match target="font" >
<test name="family" compare="contains" >
<string>Song</string>
<string>Sun</string>
<string>Kai</string>
<string>Ming</string>
<string>&#23435;&#20307;</string>
<string>&#23435;&#20307;-18030</string>
<string>&#40657;&#20307;</string>
<string>&#26032;&#23435;&#20307;</string>
<string>&#26032;&#23435;&#20307;-18030</string>
<string>&#26999;&#20307;_GB2312</string>
<string>&#20223;&#23435;_GB2312</string>
<string>&#38582;&#20307;</string>
<string>SimSun</string>
<string>SimSun-18030</string>
<string>SimHei</string>
<string>NSimSun</string>
<string>NSimSun-18030</string>
<string>KaiTi_GB2312</string>
<string>FangSong_GB2312</string>
<string>LiSu</string>
</test>

<edit name="globaladvance">

<bool>false</bool>

</edit>

<edit name="spacing">

<int>0</int>

</edit>

<edit name="hinting">

<bool>true</bool>

</edit>

<edit name="autohint">

<bool>false</bool>

</edit>

<edit name="antialias" mode="assign">

<bool>true</bool>

</edit>

<test name="pixelsize" compare="more_eq">

<int>12</int>

</test>
<test name="pixelsize" compare="less_eq">

<int>24</int>

</test>
<edit name="antialias" mode="assign" >

<bool>false</bool>

</edit>
</match>
</fontconfig>


but the problem is that the english fonts in firefox looks ugly, and in viture terminal, it's more ugly, sometimes unreadable.
1. how can I keep the chinese fonts, but change the english fonts to the ubuntu orginal(default) one ?

2. how to install MS fonts ? so that the openoffice documents made here can keep it's orginal style when some MS office open it in windows ?

3. i also have another user no need chinese support, anyway to set a sets of font rules to that individual user ? if yes, how to please ?

thankx for your help in advnaced.

---

### Post by danbuntu on 2006-07-21
attached a terminal window.
many characters unreadable.
please help.

---

