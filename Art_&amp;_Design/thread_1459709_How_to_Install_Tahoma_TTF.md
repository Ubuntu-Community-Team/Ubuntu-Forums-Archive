---
title: "How to Install Tahoma TTF"
date: 2010-04-21
forum: Art &amp; Design
---

### Post by trentscott on 2010-04-21
If anyone's interested, I stumbled on this from MasterProg:

Here's a shell script I made to do this automatically. It installs  msttcorefonts package and downloads and installs Tahoma font. After that  font cache is rebuilt.


```
#!/bin/bash
# Install Microsoft Fonts (Including Tahoma)

if [ "$(id -u)" == "0" ]
then
  if apt-get install msttcorefonts; then
    mkdir temp-tahomafont
    cd temp-tahomafont
    if wget  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IELPKTH.CAB;  then
      cabextract IELPKTH.CAB
      if cp *.ttf /usr/share/fonts/truetype/msttcorefonts/; then
        if fc-cache -fv; then
          cd ..
          rm -r temp-tahomafont
          echo "Microsoft fonts are now installed"
        else
          echo "Could not rebuild font cache"
          exit -1
        fi
      else
        echo "Could not copy the font to  /usr/share/fonts/truetype/msttcorefonts/"
        exit -1
      fi
    else
      echo "Could not download Tahoma font"
      exit -1
    fi
  else
    echo "Could not install msttcorefonts package" 
    exit -1
  fi
else
  echo "Run 'sudo ./addfonts.sh'"
  exit 0
fi
```


Save it as 'addfonts.sh', allow it to execute: chmod +x addfonts.sh and  then run it as root: sudo ./addfonts.sh

---

### Post by mlkovacs on 2010-04-21
> **trentscott said:**
> If anyone's interested, I stumbled on this from MasterProg:

Here's a shell script I made to do this automatically. It installs  msttcorefonts package and downloads and installs Tahoma font. After that  font cache is rebuilt.


```
#!/bin/bash
# Install Microsoft Fonts (Including Tahoma)

if [ "$(id -u)" == "0" ]
then
  if apt-get install msttcorefonts; then
    mkdir temp-tahomafont
    cd temp-tahomafont
    if wget  http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IELPKTH.CAB;  then
      cabextract IELPKTH.CAB
      if cp *.ttf /usr/share/fonts/truetype/msttcorefonts/; then
        if fc-cache -fv; then
          cd ..
          rm -r temp-tahomafont
          echo "Microsoft fonts are now installed"
        else
          echo "Could not rebuild font cache"
          exit -1
        fi
      else
        echo "Could not copy the font to  /usr/share/fonts/truetype/msttcorefonts/"
        exit -1
      fi
    else
      echo "Could not download Tahoma font"
      exit -1
    fi
  else
    echo "Could not install msttcorefonts package" 
    exit -1
  fi
else
  echo "Run 'sudo ./addfonts.sh'"
  exit 0
fi
```


Save it as 'addfonts.sh', allow it to execute: chmod +x addfonts.sh and  then run it as root: sudo ./addfonts.sh

I get a syntax error:
```
./addfonts.sh: line 6: syntax error near unexpected token `then'
./addfonts.sh: line 6: `* if apt-get install msttcorefonts; then'
```

---

### Post by schoft on 2010-04-22
Worked wonderfully! I couldn't quite install the Tahoma font right, since i'm a noob. I needed it for Steam. This did the trick. Thanks

---

### Post by duanemorrison on 2010-04-23
Tahoma is a very good font. I don't think so that you need to install this font in your PC. Because this font is a part of windows how you can install again

---

### Post by ypradeep on 2010-05-29
Thanks. Did exactly as instructed. The script worked like a charm. Fonts installed correctly in Ubuntu. Thanks again. - Pradeep :)

---

### Post by jminker on 2011-10-23
Thanks! This did the trick for me, too! :)

---

