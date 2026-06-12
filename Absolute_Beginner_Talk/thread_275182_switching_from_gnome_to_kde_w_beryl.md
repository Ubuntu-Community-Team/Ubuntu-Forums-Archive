---
title: "switching from gnome to kde w/ beryl"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-10-11
i have both ubuntu-desktop and kubuntu-desktop installed. before beryl, i was able to just choose the session from the login screen. how would i log in with kde instead of gnome now that i have beryl installed?

thanks!

---

### Post by jordanmthomas on 2006-10-11
The same way you would, it should still be in the sessions menu.

You would need to start beryl-manager manually, though, or put it in your KDE Autostart folder.

---

### Post by shanepardue on 2006-10-11
for some reason i don't have a kde session available. i installed kubuntu-desktop with aptitude and everything went just fine on that side of things. i did notice that when i right-click beryl settings, it shows Kwin (KDE Window Manager). any ideas?

---

### Post by jordanmthomas on 2006-10-11
```
[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=/usr/bin/startkde
TryExec=/usr/bin/startkde
Name=KDE
Comment=The K Desktop Environment. A powerful Open Source graphical desktop environment
X-Ubuntu-Gettext-Domain=desktop_kdebase
```

```
sudo touch /usr/share/xsessions/kde.desktop
sudo nano /usr/share/xsessions/kde.desktop 
```

Paste the above code in there.
Then, is kde on your gdm screen?

---

### Post by shanepardue on 2006-10-11
i'm sorry...am i entering the below commands then pasting the code? if not, where does that code go? i'm not home to try it out and i wanted to clear that up before then. thanks!

---

### Post by jordanmthomas on 2006-10-11
Enter the commands (with sudo) and a texst editor will come up.
Then paste in the [Desktop Entry] stuff and save it.

You should then have a KDE entry in gdm

---

### Post by shanepardue on 2006-10-11
that's what i figured, but i've never messed with kde.desktop. i'll try it out tonight. thanks!

---

### Post by shanepardue on 2006-10-11
i did exactly what you said and it shows a foo entry in gdm and it fails when i attempt to login to it.

---

### Post by jordanmthomas on 2006-10-11
```
[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=/usr/bin/startkde
TryExec=/usr/bin/startkde
Name=KDE
Name[hi]=&#2325;&#2375;&#2337;&#2368;&#2312;
Name[mn]=&#1050;&#1044;&#1069;
Name[ta]=K&#2959;&#2993;&#3021;&#2993;&#2965;&#3021; &#2965;&#3006;&#2997;&#2994;&#2985;&#3021;
Name[xh]=iKDE
Name[xx]=xxKDExx
Comment=The K Desktop Environment. A powerful Open Source graphical desktop environment
Comment[bs]=K Desktop Environment. Mo&#263;an grafi&#269;ki desktop otvorenog izvornog koda
Comment[ca]=L'entorn d'escriptori K. Un poderós entorn d'escriptori gràfic de Codi Font Obert
Comment[cy]=Yr Amgylchedd Penbwrdd K.  Amgylchedd penbwrdd graffegol pwerus, sy'n gôd-agored.
Comment[da]=K Skrivebordsmiljøet. Et kraftigt, åbent, grafisk skrivebordsmiljø
Comment[de]=Das K Desktop Environment. Eine mächtige, graphische Arbeitsumgebung und Open Source / Freie Software
Comment[el]=&#932;&#959; K Desktop Environment. &#904;&#957;&#945; &#960;&#945;&#957;&#943;&#963;&#967;&#965;&#961;&#959; &#949;&#955;&#949;&#973;&#952;&#949;&#961;&#951;&#962; &#960;&#961;&#959;&#941;&#955;&#949;&#965;&#963;&#951;&#962; &#947;&#961;&#945;&#966;&#953;&#954;&#972; &#960;&#949;&#961;&#953;&#946;&#940;&#955;&#955;&#959;&#957; &#949;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945;&#962; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;
Comment[es]=El Entorno de Escritorio K, un potente entorno de escritorio gráfico realizado de código abierto
Comment[et]=K töölaua keskkond on võimas vaba tarkvara graafiline töölaua keskkond
Comment[fi]=KDE-työpöytäympäristö (K Desktop Environment) on tehokas avoimen lähdekoodin graafinen työpöytäympäristö
Comment[fr]=The K Desktop Environment. Un environnement de bureau graphique, puissant et Open Source
Comment[he]=The K Desktop Environment. &#1505;&#1489;&#1497;&#1489;&#1514; &#1506;&#1489;&#1493;&#1491;&#1492; &#1490;&#1512;&#1508;&#1497;&#1514;, &#1489;&#1506;&#1500;&#1514;-&#1506;&#1493;&#1510;&#1502;&#1492; &#1489;&#1511;&#1493;&#1491; &#1508;&#1514;&#1493;&#1495;
Comment[hi]=&#2325;&#2375; &#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2377;&#2346; &#2357;&#2366;&#2340;&#2366;&#2357;&#2352;&#2339;. &#2319;&#2325; &#2358;&#2325;&#2381;&#2340;&#2367;&#2358;&#2366;&#2354;&#2368;, &#2323;&#2346;&#2344; &#2360;&#2379;&#2352;&#2381;&#2360; &#2330;&#2367;&#2340;&#2381;&#2352;&#2350;&#2351; &#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2377;&#2346; &#2357;&#2366;&#2340;&#2366;&#2357;&#2352;&#2339;
Comment[hu]=A KDE grafikus munkakörnyezet, egy szabad forráskódú grafikus ablakkezel&#337; környezet
Comment[it]=L'ambiente desktop KDE. Un potente ambiente desktop grafico Open Source
Comment[mn]=The K Desktop Environment. &#1061;&#1199;&#1095;&#1080;&#1088;&#1093;&#1101;&#1075; &#1085;&#1101;&#1101;&#1083;&#1090;&#1090;&#1101;&#1081; &#1101;&#1093; &#1082;&#1086;&#1076; &#1073;&#1199;&#1093;&#1080;&#1081; &#1075;&#1088;&#1072;&#1092;&#1080;&#1082; &#1076;&#1101;&#1083;&#1075;&#1101;&#1094;&#1080;&#1081;&#1085; &#1086;&#1088;&#1095;&#1080;&#1085;
Comment[nb]=K Desktop Environment. Et kraftig grafisk skrivebordsmiljø med åpen kildekode.
Comment[nl]=De K Desktop Environment, een krachtige open source grafische desktop environment
Comment[nn]=K Desktop Environment. Eit kraftig grafisk skrivebordsmiljø med open kjeldekode.
Comment[pl]=&#346;rodowisko KDE. Pot&#281;&#380;ne &#347;rodowisko graficzne Wolnego Oprogramowania.
Comment[pt]=O K Desktop Environment. Um ambiente gráfico open source poderoso
Comment[pt_BR]=Acrônimo para K Desktop Environment (ou Ambiente de Trabalho K). Um poderoso ambiente de trabalho gráfico de código aberto
Comment[ro]=K Desktop Environment. Un mediu grafic cu surse deschise, foarte puternic
Comment[sk]=The K Desktop Environment. Výkonné, vo&#318;ne &#353;írite&#318;né grafické pracovné prostredie
Comment[sl]=Namizno okolje K. Zmogljivo grafi&#269;no namizno okolje odprte kode
Comment[sr]=K Desktop Environment (KDE). &#1052;&#1086;&#1115;&#1085;&#1086; &#1075;&#1088;&#1072;&#1092;&#1080;&#1095;&#1082;&#1086; &#1088;&#1072;&#1076;&#1085;&#1086; &#1086;&#1082;&#1088;&#1091;&#1078;&#1077;&#1114;&#1077; &#1086;&#1090;&#1074;&#1086;&#1088;&#1077;&#1085;&#1086;&#1075; &#1082;&#1086;&#1076;&#1072;
Comment[sv]=K-skrivbordsmiljön. En kraftfull grafisk skrivbordsmiljö med öppen källkod
Comment[ta]= K&#2990;&#3015;&#2994;&#3021;&#2990;&#3015;&#2970;&#3016; &#2970;&#3010;&#2996;&#2994;&#3021;. &#2970;&#2965;&#3021;&#2980;&#3007;&#2997;&#3006;&#2991;&#3021;&#2984;&#3021;&#2980; &#2980;&#3007;&#2993;&#2984;&#3021;&#2980; &#2950;&#2979;&#3016;&#2990;&#3010;&#2994; &#2970;&#3007;&#2980;&#3021;&#2980;&#3007;&#2992; &#2997;&#2965;&#3016; &#2990;&#3015;&#2994;&#3021;&#2990;&#3015;&#2970;&#3016; &#2970;&#3010;&#2996;&#2994;&#3021;
Comment[tr]=KDE Masaüstü Yöneticisi. Güçlü bir grafiksel masaüstü ortam&#305;
Comment[uk]=The K Desktop Environment. &#1055;&#1086;&#1090;&#1091;&#1078;&#1085;&#1077; &#1075;&#1088;&#1072;&#1092;&#1110;&#1095;&#1085;&#1077; &#1089;&#1077;&#1088;&#1077;&#1076;&#1086;&#1074;&#1080;&#1097;&#1077; &#1079; &#1074;&#1110;&#1076;&#1082;&#1088;&#1080;&#1090;&#1080;&#1084;&#1080; &#1090;&#1077;&#1082;&#1089;&#1090;&#1072;&#1084;&#1080;
Comment[uz]=KDE (K Desktop Environment) - &#1082;&#1091;&#1095;&#1083;&#1080; Open Source &#1075;&#1088;&#1072;&#1092;&#1080;&#1082; &#1080;&#1096; &#1089;&#1090;&#1086;&#1083;&#1080; &#1084;&#1091;&#1203;&#1080;&#1090;&#1080;
Comment[vi]=môi tr&#432;&#7901;ng desktop K, môi tr&#432;&#7901;ng desktop &#273;&#7891; ho&#7841; mã ngu&#7891;n m&#7903; r&#7845;t m&#7841;nh
Comment[xx]=xxThe K Desktop Environment. A powerful Open Source graphical desktop environmentxx
Comment[zh_CN]=K &#26700;&#38754;&#29615;&#22659;&#12290;&#24378;&#22823;&#30340;&#24320;&#25918;&#28304;&#20195;&#30721;&#22270;&#24418;&#26700;&#38754;&#29615;&#22659;
X-Ubuntu-Gettext-Domain=desktop_kdebase
```

Is what mine looks like exactly

maybe your permissions are wrong...mine look like this
```
-rw-r--r-- 1 root root 3932 2006-10-07 06:54 kde.desktop
```

Maybe you should try to reconfigure kubuntu-desktop
```
sudo dpkg-reconfigure kubuntu-desktop
```

Sorry, I don't really know anything else to try.

---

### Post by sunny_nwho on 2006-10-13
Hi even I am having problem with beryl in KDE 3.5.5 yesterdya i removed my gnome which was working perfectly with beryl and installed KDE upgraded to 3.5.5 and then installed beryl and it wont start i get the error 
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

I followed the instructions from wiki.beryl-project and it ran well in gnome...i wonder whts the problem with KDE

Somebody please help

---

