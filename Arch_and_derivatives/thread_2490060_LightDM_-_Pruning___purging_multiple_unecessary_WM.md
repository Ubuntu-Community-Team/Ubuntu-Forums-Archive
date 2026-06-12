---
title: "LightDM - Pruning /  purging multiple unecessary WM options"
date: 2023-08-21
forum: Arch and derivatives
---

### Post by Drone4four on 2023-08-21
What is with ldm WM (Gnome) options? When I select the WM options menu in ldm, this is what I see: [https://i.imgur.com/1bz956w.jpg](https://i.imgur.com/1bz956w.jpg)

I understand, accept, and am happy to see these options at the bottom:

> 
GNOME on Xorg
GNOME on Wayland


But that should be it. Next you can see:

> 
GNOME Classic on Xorg
GNOME Classic on Wayland


I am uninterested in running Classic versions of Gnome.

What happens next is really strange:

> 
GNOME Classic
GNOME Classic
GNOME
GNOME


It doesn't specify which protocol, whether Xorg or Wayland.

How do I prune / delete / remove all of these redundant and non-descript options?

---

### Post by Holger_Gehrke on 2023-08-21
There should be .desktop files for sessions in '/usr/share/xsessions/'. Moving them out of that directory should remove them from the list. You can tell which file is which by checking the 'name=' lines in the files.

Holger

---

### Post by Drone4four on 2023-08-29
Here are the contents of /usr/share/xsessions:

```
$ pwd
/usr/share/xsessions
$ ls -la
total 28
drwxr-xr-x   3 root root  4096 Aug 29 16:46 .
drwxr-xr-x 362 root root 12288 Aug 29 16:46 ..
drwxr-xr-x   2 root root  4096 Aug 21 04:51 bax2k23Aug21
-rw-r--r--   1 root root  7915 Apr  9 19:56 gnome-xorg.desktop
```

Rather than deleting/removing, I just created a backup directory and moved all the ones I didn't like into them like so:

```
$ cd bax2k23Aug21 
$ pwd
/usr/share/xsessions/bax2k23Aug21
$ ls -la
total 44
drwxr-xr-x 2 root root 4096 Aug 21 04:51 .
drwxr-xr-x 3 root root 4096 Aug 29 16:46 ..
-rw-r--r-- 1 root root  984 Aug 10 18:08 e16-gnome2-session.desktop
-rw-r--r-- 1 root root  211 Aug 10 18:08 e16-gnome3-session.desktop
-rw-r--r-- 1 root root  969 Aug 10 18:08 e16-kde-session.desktop
-rw-r--r-- 1 root root 8139 Apr 28 20:21 gnome-classic.desktop
-rw-r--r-- 1 root root 7617 Apr 28 20:21 gnome-classic-xorg.desktop
-rw-r--r-- 1 root root 7830 Apr  9 19:56 gnome.desktop
```

So I did what you recommended, **@AgoHolger_Gehrke**. Some of the options are gone. Thank you. See here: [https://imgur.com/a/3gvBJUf](https://imgur.com/a/3gvBJUf). That's progress. But there are some that are still not necessary.  

ldm now presents:
> GNOME
GNOME Classic
GNOME Classic on Wayland
GNOME on Wayland
GNOME on Xorg

How do I prune these further so that I only see:
> GNOME on Wayland
GNOME on Xorg

How do I get rid of all those "Classic" options as well as the non-descript "GNOME"?

Where else on a Linux system with ldm as the greeter might configurations be stored for me to change to achieve the desired end result?

---

### Post by #&amp;thj^% on 2023-08-29
for myself I just:
```
ls /usr/share/xsessions/
kodi.desktop  xfce.desktop

```
remove the one I don't want::
```
sudo rm /usr/share/xsessions/kodi.desktop

```
a check with:
```
ls /usr/share/xsessions/
xfce.desktop

```
BTW Kodi still works I just want cleared out of view.

**[COLOR="#FF0000"]BUT THE BEST is to back it up:[/COLOR]**
```
sudo mv /usr/share/xsessions/gnome-classic.desktop gnome-classic.desktop.backup

```

---

### Post by Drone4four on 2023-08-29
Hi **@Ago1fallen,** Thank you for your reply. Although you recommend that I remove or backup the `.desktop` files in `/usr/share/xsessions` that I do not want. Not sure if you ready my most recent post, but I thought I explained I already tried what you said and it is still not working for me.

---

### Post by #&amp;thj^% on 2023-08-29
This is where they are stored, *something else is in the way then, and yes i read your post #3
So show us this:
```
apt policy gdm3

```

---

### Post by Holger_Gehrke on 2023-08-30
Two things I'd try:
1. Take a look at the contents of the desktop file you've left in the directory (normal desktop files should only define exactly one item, but who knows ... ; .desktop files are just normal text files, so 'less' or your favourite editor will work).
2. Move the backups somewhere outside of /usr/share/xsessions in case the search for desktop files is recursive

Holger

---

### Post by Drone4four on 2023-09-04
> **Holger_Gehrke said:**
> Two things I'd try:
Move the backups somewhere outside of /usr/share/xsessions in case the search for desktop files is recursive


Thank you for the suggestion **@Holger_Gehrke**. I moved the backups out from /usr/share/xessions into my home directory. The contents of /usr/share/xessions now look like this:

```
$ cd /usr/share/xsessions 
$ ls -la
total 24
drwxr-xr-x   2 root root  4096 Sep  4 07:57 .
drwxr-xr-x 362 root root 12288 Sep  4 07:56 ..
-rw-r--r--   1 root root  7915 Apr  9 19:56 gnome-xorg.desktop
```

I rebooted. ldm is still presenting 3 unnecessary entries:

> GNOME
GNOME Classic
GNOME Classic on Wayland
GNOME on Wayland
GNOME on Xorg

I am still trying to get ldm to only present the final 2 in the above list.

> Take a look at the contents of the desktop file you've left in the directory (normal desktop files should only define exactly one item, but who knows ... ; .desktop files are just normal text files, so 'less' or your favourite editor will work).
 
Here are the contents of that one and only `gnome-xorg.desktop` file in `/usr/share/xessions/`:

```
[Desktop Entry]
Name[ab]=GNOME  Xorg &#1072;&#1183;&#1085;&#1099;
Name[af]=GNOME op Xorg
Name[an]=GNOME en Xorg
Name[be]=GNOME &#1085;&#1072; Xorg
Name[bg]=GNOME &#1089; Xorg
Name[bn_IN]=Xorg &#2447; &#2460;&#2495;&#2472;&#2507;&#2478;
Name[ca]=GNOME damunt Xorg
Name[ca@valencia]=GNOME en Xorg
Name[cs]=GNOME na Xorg
Name[da]=GNOME på Xorg
Name[de]=GNOME unter Xorg
Name[el]=GNOME &#963;&#949; Xorg
Name[en_GB]=GNOME on Xorg
Name[eo]=GNOME je Xorg
Name[es]=GNOME en Xorg
Name[et]=GNOME Xorg’iga
Name[eu]=GNOME Xorg gainean
Name[fa]=&#1711;&#1606;&#1608;&#1605; &#1585;&#1608;&#1740; &#1586;&#1608;&#1585;&#1711;
Name[fi]=Gnome Xorgia käyttäen
Name[fr]=GNOME sur Xorg
Name[fur]=GNOME su Xorg
Name[gd]=GNOME air Xorg
Name[gl]=GNOME en Xorg
Name[gu]=Xorg &#2730;&#2736; GNOME
Name[he]=&#8207;GNOME &#1506;&#1500; &#1490;&#1489;&#1497; Xorg
Name[hr]=GNOME na Xorgu
Name[hu]=GNOME Xorgon
Name[id]=GNOME pada Xorg
Name[is]=GNOME á Xorg
Name[it]=GNOME su Xorg
Name[ja]=GNOME on Xorg
Name[ka]=GNOME Xorg-&#4310;&#4308;
Name[kab]=GNOME &#611;ef Xorg
Name[kk]=Xorg &#1085;&#1077;&#1075;&#1110;&#1079;&#1110;&#1085;&#1076;&#1077;&#1075;&#1110; GNOME
Name[ko]=&#44536;&#45448; (Xorg)
Name[lt]=GNOME Xorg aplinkoje
Name[lv]=GNOME ar Xorg
Name[mjw]=GNOME on Xorg
Name[ml]=&#3351;&#3405;&#3368;&#3403;&#3330; Xorg &#3378;&#3405;*
Name[ms]=GNOME di Xorg
Name[nb]=GNOME på Xorg
Name[ne]=Xorg &#2350;&#2366; &#2332;&#2367;&#2344;&#2379;&#2350;
Name[nl]=Gnome op Xorg
Name[oc]=GNOME sus Xorg
Name[pa]=Xorg &#2569;&#2673;&#2596;&#2631; &#2583;&#2600;&#2635;&#2606;
Name[pl]=GNOME (Xorg)
Name[pt]=GNOME em Xorg
Name[pt_BR]=GNOME sobre Xorg
Name[ro]=GNOME pe Xorg
Name[ru]=GNOME &#1085;&#1072; Xorg
Name[sk]=GNOME cez Xorg
Name[sl]=GNOME na sistemu Xorg
Name[sr]=&#1043;&#1085;&#1086;&#1084; &#1085;&#1072; &#1048;&#1082;&#1089; &#1089;&#1077;&#1088;&#1074;&#1077;&#1088;&#1091;
Name[sr@latin]=Gnom na Iks serveru
Name[sv]=GNOME med Xorg
Name[th]=GNOME &#3651;&#3609; Xorg
Name[tr]=Xorg üzerinde GNOME
Name[uk]=GNOME &#1095;&#1077;&#1088;&#1077;&#1079; Xorg
Name[zh_CN]=GNOME Xorg
Name[zh_TW]=GNOME &#25505;&#34892; Xorg
Name=GNOME on Xorg
Comment[ab]=&#1040;&#1088;&#1080; &#1072;&#1089;&#1077;&#1072;&#1085;&#1089; GNOME &#1072;&#1197;&#1072;&#1083;&#1072;&#1088;&#1072; &#1072;&#1079;&#1080;&#1085; &#1096;&#1241;&#1085;&#1072;&#1197;&#1086;&#1080;&#1090; 
Comment[af]=Die sessie laat u by GNOME aanmeld
Comment[an]=Ista sesión accede a GNOME
Comment[ar]=&#1578;&#1608;&#1604;&#1580;&#1603; &#1607;&#1584;&#1607; &#1575;&#1604;&#1580;&#1604;&#1587;&#1577; &#1601;&#1610; &#1580;&#1606;&#1608;&#1605;
Comment[as]=&#2447;&#2439; &#2437;&#2471;&#2495;&#2476;&#2503;&#2486;&#2472;&#2503; &#2438;&#2474;&#2507;&#2472;&#2494;&#2453; GNOME &#2468; &#2482;&#2455;&#2495;&#2472; &#2453;&#2544;&#2494;&#2527;
Comment[ast]=Esta sesión conéuta-y a GNOME
Comment[be]=&#1057;&#1077;&#1072;&#1085;&#1089; &#1091;&#1074;&#1072;&#1093;&#1086;&#1076;&#1091; &#1118; GNOME
Comment[be@latin]=Hetaja sesija &#365;ruchamlaje GNOME
Comment[bg]=&#1042;&#1083;&#1080;&#1079;&#1072;&#1085;&#1077; &#1074; GNOME
Comment[bn]=&#2447;&#2439; &#2488;&#2503;&#2486;&#2472;&#2503;&#2480; &#2478;&#2494;&#2471;&#2509;&#2479;&#2478;&#2503; GNOME-&#2447; &#2482;&#2455;-&#2439;&#2472; &#2453;&#2480;&#2494; &#2479;&#2494;&#2476;&#2503;
Comment[bn_IN]=&#2447;&#2439; &#2488;&#2503;&#2486;&#2494;&#2472;&#2503;&#2480; &#2478;&#2494;&#2471;&#2509;&#2479;&#2478;&#2503; GNOME-&#2447; &#2482;&#2455;-&#2439;&#2472; &#2453;&#2480;&#2494; &#2479;&#2494;&#2476;&#2503;
Comment[br]=An estez-mañ a lug ac'hanoc'h davet GNOME
Comment[bs]=Ova sesija Vas prijavljuje u GNOME
Comment[ca]=Aquesta sessió us entra al GNOME
Comment[ca@valencia]=Esta sessió vos entra al GNOME
Comment[ckb]=&#1576;&#1607;*&#1605; &#1583;&#1575;&#1606;&#1740;&#1588;&#1578;&#1606;&#1607;* &#1574;&#1607;*&#1705;&#1607;*&#1608;&#1740;&#1578;&#1607;* &#1606;&#1575;&#1608; &#1711;&#1606;&#1608;&#1605;&#1607;*&#1608;&#1607;*
Comment[crh]=Bu otur&#305;m sizni GNOME'&#287;a içeri imzaland&#305;r&#305;r
Comment[cs]=Toto sezení vás p&#345;ihlásí do GNOME
Comment[da]=Denne session logger dig ind i GNOME
Comment[de]=Diese Sitzung meldet Sie bei GNOME an
Comment[dz]=&#3939;&#3953;&#3851;&#3937;&#3956;&#3923;&#3851;&#3936;&#3921;&#3954;&#3851;&#3906;&#3954;&#3942;&#3851; &#3905;&#4017;&#3964;&#3921;&#3851; &#3911;&#3954;&#3851;&#3923;&#3964;&#3928;&#3851;&#3923;&#3908;&#3851;&#3939;&#3956;&#3851; &#3923;&#3908;&#3851;&#3926;&#3942;&#3984;&#4017;&#3964;&#3921;&#3851;&#3936;&#3926;&#3921;&#3933;&#3851;&#3944;&#3954;&#3923;&#3851; 
Comment[el]=&#913;&#965;&#964;&#942; &#951; &#963;&#965;&#957;&#949;&#948;&#961;&#943;&#945; &#963;&#945;&#962; &#963;&#965;&#957;&#948;&#941;&#949;&#953; &#963;&#964;&#959; GNOME
Comment[en_GB]=This session logs you into GNOME
Comment[en@shaw]=&#66654;&#66662;&#66645; &#66645;&#66663;&#66646;&#66665;&#66671; &#66660;&#66666;&#66652;&#66655; &#66687; &#66662;&#66671;&#66641;&#66667; ·&#66652;&#66671;&#66676;&#66661;
Comment[eo]=&#264;i tiu seanco salutas vin en GNOME
Comment[es]=Esta sesión accede a GNOME
Comment[et]=Selle seansiga logitakse sind GNOME keskkonda sisse
Comment[eu]=Saio honek GNOMEn sartuko zaitu
Comment[fa]=&#1575;&#1740;&#1606; &#1606;&#1588;&#1587;&#1578; &#1588;&#1605;&#1575; &#1585;&#1575; &#1576;&#1607; &#1711;&#1606;&#1608;&#1605; &#1608;&#1575;&#1585;&#1583; &#1605;&#1740;*&#1705;&#1606;&#1583;
Comment[fi]=Tämä istunto kirjautuu Gnomeen
Comment[fr]=Cette session vous connecte dans GNOME
Comment[fur]=Cheste session ti fasarà jentrâ in GNOME
Comment[fy]=Dizze sesje meld jo oan by Gnome
Comment[ga]=Logálann an seisiún seo thú isteach i nGNOME
Comment[gd]=Clàraidh an seisean seo a-steach gu GNOME thu
Comment[gl]=Esta sesión iniciará en GNOME
Comment[gu]=&#2694; &#2744;&#2724;&#2765;&#2736; &#2724;&#2734;&#2728;&#2759; GNOME &#2734;&#2750;&#2690; &#2730;&#2765;&#2736;&#2741;&#2759;&#2742; &#2694;&#2730;&#2759; &#2715;&#2759;
Comment[he]=&#1492;&#1508;&#1506;&#1500;&#1492; &#1494;&#1488;&#1514; &#1502;&#1495;&#1489;&#1512;&#1514; &#1488;&#1493;&#1514;&#1498; &#1500;&#1513;&#1493;&#1500;&#1495;&#1503; &#1492;&#1506;&#1489;&#1493;&#1491;&#1492; GNOME
Comment[hi]=&#2351;&#2361; &#2360;&#2340;&#2381;&#2352; &#2327;&#2344;&#2379;&#2350; &#2350;&#2375;&#2306; &#2354;&#2377;&#2327;&#2311;&#2344; &#2361;&#2379;&#2327;&#2366;
Comment[hr]=Ova sesija vas prijavljuje u GNOME
Comment[hu]=Bejelentkezés a GNOME környezetbe
Comment[id]=Sesi ini melogkan Anda ke dalam GNOME
Comment[ie]=Ti es li session de GNOME
Comment[is]=Þessi seta skráir þig inn í GNOME
Comment[it]=Questa sessione esegue l'accesso in GNOME
Comment[ja]=&#12371;&#12398;&#12475;&#12483;&#12471;&#12519;&#12531;&#12391; GNOME &#12395;&#12525;&#12464;&#12452;&#12531;&#12375;&#12414;&#12377;
Comment[ka]=&#4304;&#4325;&#4308;&#4307;&#4304;&#4316; &#4328;&#4308;&#4334;&#4309;&#4304;&#4314;&#4311; GNOME-&#4328;&#4312;
Comment[kab]=Ti&#611;imit-agi ad k-teqqen &#611;er GNOME
Comment[kk]=&#1041;&#1201;&#1083; &#1089;&#1077;&#1089;&#1089;&#1080;&#1103; &#1072;&#1088;&#1179;&#1099;&#1083;&#1099; GNOME-&#1171;&#1072; &#1082;&#1110;&#1088;&#1077;&#1089;&#1110;&#1079;
Comment[km]=&#6047;&#6040;&#6096;&#6041;&#8203;&#6035;&#6081;&#6087;&#8203;&#6023;&#6070;&#8203;&#6016;&#6086;&#6030;&#6031;&#6091;&#8203;&#6048;&#6081;&#6031;&#6075;&#8203;&#6026;&#6082;&#6043;&#8203;&#6050;&#6098;&#6035;&#6016;&#8203;&#6033;&#6085;&#8203;&#6016;&#6070;&#6035;&#6091; GNOME
Comment[kn]=&#3208; &#3205;&#3239;&#3263;&#3253;&#3271;&#3254;&#3240;&#3253;&#3265; &#3240;&#3263;&#3246;&#3277;&#3246;&#3240;&#3277;&#3240;&#3265; GNOME &#3223;&#3270; &#3242;&#3277;&#3248;&#3253;&#3271;&#3254;&#3263;&#3256;&#3265;&#3253;&#3202;&#3236;&#3270; &#3246;&#3262;&#3233;&#3265;&#3236;&#3277;&#3236;&#3238;&#3270;
Comment[ko]=&#51060; &#49464;&#49496;&#51012; &#49324;&#50857;&#54616;&#47732; &#44536;&#45448;&#50640; &#47196;&#44536;&#51064;&#54633;&#45768;&#45796;
Comment[lt]=Šis seansas prijungia jus prie GNOME
Comment[lv]=Š&#299; sesija ieraksta j&#363;s GNOME vid&#275;
Comment[mai]=&#2312; &#2360;&#2340;&#2381;&#2352; &#2309;&#2361;&#2366;&#2305;&#2325; &#2327;&#2344;&#2379;&#2350;&#2350;&#2375; &#2354;&#2366;&#2327;&#2367;&#2344; &#2342;&#2376;&#2331;
Comment[mjw]=Laso session nangli phan GNOME long pon po
Comment[mk]=&#1054;&#1074;&#1072;&#1072; &#1089;&#1077;&#1089;&#1080;&#1112;&#1072; &#1042;&#1077; &#1085;&#1072;&#1112;&#1072;&#1074;&#1091;&#1074;&#1072; &#1074;&#1086; GNOME
Comment[ml]=&#3336; &#3370;&#3405;&#3376;&#3381;&#3376;&#3405;*&#3364;&#3405;&#3364;&#3368;&#3381;&#3399;&#3379; &#3368;&#3391;&#3353;&#3405;&#3353;&#3379;&#3398; &#3351;&#3405;&#3368;&#3403;&#3374;&#3391;&#3378;&#3399;&#3349;&#3405;&#3349;&#3405; &#3349;&#3375;&#3377;&#3405;&#3377;&#3393;&#3368;&#3405;&#3368;&#3393;
Comment[mr]=GNOME &#2350;&#2343;&#2381;&#2351;&#2375; &#2342;&#2366;&#2326;&#2354; &#2325;&#2352;&#2339;&#2381;&#2351;&#2366;&#2332;&#2379;&#2327;&#2368; &#2360;&#2340;&#2381;&#2352; &#2354;&#2377;&#2327;
Comment[ms]=Sesi ini akan mendaftar masuk ke GNOME
Comment[nb]=Denne økten logger inn i GNOME
Comment[nds]=Düsser Törn mellt dik bi GNOME an
Comment[ne]=&#2351;&#2379; &#2360;&#2340;&#2381;&#2352; &#2332;&#2367;&#2344;&#2379;&#2350; &#2354;&#2327;&#2312;&#2344; &#2361;&#2369;&#2344;&#2381;&#2331;
Comment[nl]=Deze sessie laat u in Gnome inloggen
Comment[nn]=Denne økta loggar inn i GNOME
Comment[oc]=Aquesta session vos connècta dins GNOME
Comment[or]=&#2831;&#2873;&#2879; &#2821;&#2855;&#2879;&#2860;&#2887;&#2870;&#2856; &#2822;&#2858;&#2851;&#2841;&#2893;&#2837;&#2881; &#2856;&#2891;&#2862; &#2864;&#2887; &#2866;&#2839; &#2837;&#2864;&#2878;&#2823;&#2853;&#2878;&#2831;
Comment[pa]=&#2567;&#2617; &#2616;&#2620;&#2632;&#2616;&#2620;&#2600; &#2596;&#2625;&#2617;&#2622;&#2600;&#2626;&#2672; &#2583;&#2600;&#2635;&#2606; &#2613;&#2623;&#2673;&#2586; &#2610;&#2622;&#2583; &#2581;&#2608;&#2598;&#2622; &#2617;&#2632;
Comment[pl]=Ta sesja loguje u&#380;ytkownika do &#347;rodowiska GNOME
Comment[ps]=&#1583;&#1575; &#1606;&#1575;&#1587;&#1578;&#1607; &#1578;&#1575;&#1587;&#1608; &#1707;&#1606;&#1608;&#1605; &#1578;&#1607; &#1606;&#1606;&#1576;&#1575;&#1587;&#1610;
Comment[pt]=Esta sessão usa o GNOME
Comment[pt_BR]=Essa sessão o leva ao GNOME
Comment[ro]=Aceast&#259; sesiune v&#259; va autentifica în GNOME
Comment[ru]=&#1069;&#1090;&#1086;&#1090; &#1089;&#1077;&#1072;&#1085;&#1089; &#1087;&#1086;&#1079;&#1074;&#1086;&#1083;&#1103;&#1077;&#1090; &#1074;&#1072;&#1084; &#1074;&#1086;&#1081;&#1090;&#1080; &#1074; GNOME
Comment[sk]=Táto relácia vás prihlási do GNOME
Comment[sl]=Seja omogo&#269;a prijavo v namizje GNOME.
Comment[sr]=&#1054;&#1074;&#1072; &#1089;&#1077;&#1089;&#1080;&#1112;&#1072; &#1074;&#1072;&#1089; &#1087;&#1088;&#1080;&#1112;&#1072;&#1074;&#1113;&#1091;&#1112;&#1077; &#1091; &#1043;&#1085;&#1086;&#1084;
Comment[sr@latin]=Ova sesija vas prijavljuje u Gnom
Comment[sv]=Denna session loggar in dig i GNOME
Comment[ta]=&#2951;&#2984;&#3021;&#2980; &#2949;&#2990;&#2992;&#3021;&#2997;&#3009; &#2965;&#3021;&#2984;&#3019;&#2990;&#3021; &#2951;&#2994;&#3021; &#2953;&#2969;&#3021;&#2965;&#2995;&#3016; &#2984;&#3009;&#2996;&#3016;&#2965;&#3021;&#2965;&#3009;&#2990;&#3021; 
Comment[te]=&#3080; &#3128;&#3142;&#3127;&#3112;&#3149; &#3095;&#3149;&#3112;&#3147;&#3118;&#3149;*&#3122;&#3147;&#3112;&#3135;&#3093;&#3135; &#3122;&#3134;&#3095;&#3149; &#3098;&#3143;&#3128;&#3149;&#3108;&#3137;&#3074;&#3110;&#3135;
Comment[tg]=&#1048;&#1085; &#1207;&#1072;&#1083;&#1072;&#1089;&#1072; &#1096;&#1091;&#1084;&#1086;&#1088;&#1086; &#1073;&#1072; GNOME &#1074;&#1086;&#1088;&#1080;&#1076; &#1084;&#1077;&#1082;&#1091;&#1085;&#1072;&#1076;
Comment[th]=&#3623;&#3634;&#3619;&#3632;&#3609;&#3637;&#3657;&#3592;&#3632;&#3648;&#3586;&#3657;&#3634;&#3626;&#3641;&#3656; GNOME
Comment[tr]=Bu oturum GNOME’a girmenizi sa&#287;lar
Comment[ug]=&#1576;&#1735; &#1574;&#1749;&#1709;&#1711;&#1609;&#1605;&#1749; &#1587;&#1609;&#1586;&#1606;&#1609; &#1711;&#1609;&#1606;&#1608;&#1605;&#1594;&#1575; &#1574;&#1749;&#1603;&#1609;&#1585;&#1609;&#1583;&#1735;.
Comment[uk]=&#1062;&#1077; — &#1089;&#1077;&#1072;&#1085;&#1089; &#1074;&#1093;&#1086;&#1076;&#1091; &#1074; GNOME
Comment[uz]=Ushbu seans GNOME'ga kirishingizni ta&#700;minlaydi
Comment[uz@cyrillic]=&#1059;&#1096;&#1073;&#1091; &#1089;&#1077;&#1072;&#1085;&#1089; GNOME'&#1075;&#1072; &#1082;&#1080;&#1088;&#1080;&#1096;&#1080;&#1085;&#1075;&#1080;&#1079;&#1085;&#1080; &#1090;&#1072;&#1098;&#1084;&#1080;&#1085;&#1083;&#1072;&#1081;&#1076;&#1080;
Comment[zh_CN]=&#27492;&#20250;&#35805;&#23558;&#35753;&#24744;&#30331;&#24405;&#21040; GNOME
Comment[zh_HK]=&#36889;&#20491;&#20316;&#26989;&#38542;&#27573;&#35731;&#20320;&#30331;&#20837; GNOME
Comment[zh_TW]=&#36889;&#20491;&#24037;&#20316;&#38542;&#27573;&#35731;&#24744;&#30331;&#20837; GNOME
Comment=This session logs you into GNOME
Exec=/usr/bin/gnome-session
TryExec=/usr/bin/gnome-session
Type=Application
DesktopNames=GNOME
X-GDM-SessionRegisters=true
```

As you can see above, there are no instances of GNOME Classic (which are the entries I am trying to get rid of).

**@1fallen** writes:

> So show us this:
```
$ apt policy gdm3
```

Ok it is time for me to come clean. I am not actually running Ubuntu. I am not even running another Linux distro with advanced package tool. I'm running Manjaro. I know you guys are going to kill me but please understand that the reason why I reached out here on the Ubuntu forums is that lightdm-gtk-greeter is a Xubuntu native project. See here: [https://github.com/Xubuntu/lightdm-gtk-greeter](https://github.com/Xubuntu/lightdm-gtk-greeter)

I was hoping that Ubuntu forum members might be able to lend their expertise to configuring lightdm which is a distro agnostic app which is maintained by Ubuntu-related developers.

---

### Post by #&amp;thj^% on 2023-09-04
> **Drone4four said:**
> 
Ok it is time for me to come clean. I am not actually running Ubuntu. I am not even running another Linux distro with advanced package tool. I'm running Manjaro. I know you guys are going to kill me but please understand that the reason why I reached out here on the Ubuntu forums is that lightdm-gtk-greeter is a Xubuntu native project. See here: [https://github.com/Xubuntu/lightdm-gtk-greeter](https://github.com/Xubuntu/lightdm-gtk-greeter)

I was hoping that Ubuntu forum members might be able to lend their expertise to configuring lightdm which is a distro agnostic app which is maintained by Ubuntu-related developers.
That just was a good thing to know beforehand, and I just don't know Manjaro, I know Arch very well though and it still uses the same recommends or suggestions Holgre and I have used ie:
```
cd /usr/share/xsessions/ && ls
```
So you may have to head over to the Manjaro forum. (Something is different with LightDM on Manjaro)

---

### Post by Holger_Gehrke on 2023-09-04
Without reading the source to lightdm (and / or the greeter in use - probably lightdm-gtk-greeter) very closely, I can only assume that lightdm reads some additional desktop files beyond those in /usr/share/xsessions/. I'd try something like
```

find / -path /usr/share/applications -prune -o -path /usr/share/xsessions -prune -o -path $HOME/.local/share/applications -prune -o -iname '*.desktop'

```
This should find any .desktop files outside the three locations given (we know there are desktop files there and they are not the ones we are after). That will still give a lot of false hits, but if there are desktop files which are responsible for the sessions you see, they should be among the results. Might want to either pipe this into less or sent error output to /dev/null for the sake of readability ...

Holger

---

### Post by #&amp;thj^% on 2023-09-04
> **Holger_Gehrke said:**
> Without reading the source to lightdm (and / or the greeter in use - probably lightdm-gtk-greeter) very closely, I can only assume that lightdm reads some additional desktop files beyond those in /usr/share/xsessions/. I'd try something like
```

find / -path /usr/share/applications -prune -o -path /usr/share/xsessions -prune -o -path $HOME/.local/share/applications -prune -o -iname '*.desktop'

```
This should find any .desktop files outside the three locations given (we know there are desktop files there and they are not the ones we are after). That will still give a lot of false hits, but if there are desktop files which are responsible for the sessions you see, they should be among the results. Might want to either pipe this into less or sent error output to /dev/null for the sake of readability ...

Holger
+1 that would make sense to me.
Now for a fresh look
This is a very very Beta Arch Distro, Holgre might have the look needed with (- probably lightdm-gtk-greeter) But mine again just to test against gnome sessions as well):
```
cd /usr/share/xsessions && ls
gnome.desktop  gnome-xorg.desktop  onyx.desktop  xfce.desktop

```
I'm just going with what has already been suggested:

I'm keeping the "onyx.desktop" that's the desktop I'm currently testing now.
One item at a time:
```
sudo mv /usr/share/xsessions/gnome.desktop gnome.desktop.bk
###
sudo mv /usr/share/xsessions/gnome-xorg.desktop gnome-xorg.desktop.bk
```
Now I always look:
```
cd    /usr/share/xsessions && ls
gnome.desktop.bk  gnome-xorg.desktop.bk  onyx.desktop  xfce.desktop
```
Just for fun I'll move those two elswhere:
```
sudo mv gnome.desktop.bk /home/me/Documents
###
sudo mv gnome-xorg.desktop.bk /home/me/Documents

```
Another look:
```
ls
onyx.desktop  xfce.desktop

```
Even before the move to Documents I had only the two sessions showing.
I never use " lightdm-gtk-greeter" i remember 8 years back this was a buggy choice so I've not used it since.

---

### Post by coffeecat on 2023-09-05
> **Drone4four said:**
> 
Ok it is time for me to come clean. I am not actually running Ubuntu. I am not even running another Linux distro with advanced package tool. I'm running Manjaro.

@Drone4four, you originally posted in the General Help sub-forum, whose strapline clearly states, *"All your general support questions for Ubuntu, Kubuntu, Edubuntu, Xubuntu, Lubuntu, Ubuntu Mate, Ubuntu Budgie, Ubuntu Studio and Ubuntu Kylin."*. Unsurprisingly, Manjaro is not amongst them.

*Thread moved to **Arch and derivatives** sub-forum.*

Although we provide specific sub-forums for non-Ubuntu distros, this is merely a convenience for members - as 1fallen says, you may be better off seeking help in the Manjaro forum.

---

### Post by Drone4four on 2023-09-11
> **Holger_Gehrke said:**
> I'd try something like
```

find / -path /usr/share/applications -prune -o -path /usr/share/xsessions -prune -o -path $HOME/.local/share/applications -prune -o -iname '*.desktop'

```
This should find any .desktop files outside the three locations given (we know there are desktop files there and they are not the ones we are after). That will still give a lot of false hits, but if there are desktop files which are responsible for the sessions you see, they should be among the results. Might want to either pipe this into less or sent error output to /dev/null for the sake of readability

This was a stroke of genius, **@Holger_Gehrke**. Thank you. 

Since I wasn't sure how to pipe or highlight the right files, I exported your command into a .txt file in my home directory. I used this:

```
sudo find / -path /usr/share/applications -prune -o -path /usr/share/xsessions -prune -o -path $HOME/.local/share/applications -prune -o -iname '*.desktop' > xsession-search-2023sep10.txt
```

Next I opened `xsession-search-2023sep10.txt` in gedit. The file was some 740 lines long. Then did a Ctrl + F for: `classic.desktop` which referred to this location:

> /usr/share/wayland-sessions/gnome.desktop
/usr/share/wayland-sessions/gnome-classic.desktop
/usr/share/wayland-sessions/gnome-classic-wayland.desktop
/usr/share/wayland-sessions/gnome-wayland.desktop

It appears wayland-sessions serves the same purpose as xsessions. So I proceeded to backup files: gnome.desktop, gnome-classic.desktop, gnome-classic-wayland.desktop. And Eureka! It works! See here: [https://i.imgur.com/WLIhgCA.jpg](https://i.imgur.com/WLIhgCA.jpg)

Mission Accomplished. Thank you Holger.

---

