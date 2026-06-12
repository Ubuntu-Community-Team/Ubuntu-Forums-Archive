---
title: "PM G5 Quad und Ubuntu Mate 16.04. PPC"
date: 2017-09-17
forum: Apple Hardware Users
---

### Post by kate-libby on 2017-09-17
[COLOR=#000000][FONT=Verdana]Guten Morgen![/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Um Ubuntu zu installieren habe ich die orig. GeForce 6600 in den G5 gesteckt und 16.04. Mate installiert. Habe das mit 2 unterschiedlichen HDD´s versucht, aber in beiden Fällen läuft die Installation komplett durch und bei einem Neustart kommt der Yaboot Bootmanager und danach erscheint das Mac Ordnersymbol, welches nervig vor sich hin blinkt. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Kennt das wer? Ich würde fast vermuten, dass die HDD nicht aktiv gesetzt wurde bei der Installation. Wissen tue ich es aber nicht. 1 HDD kann ja einen Hauweg haben, aber Beide? Zumal beide HDD´s unter Leopard anstandslos funktionieren.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Ich weiß nicht weiter.[/FONT][/COLOR]

---

### Post by ernsteiswuerfel on 2018-01-25
Falls das noch von Bedeutung ist nach der langen Zeit: Ja, das ist ein yaboot Problem. Der Installer kriegt die automatische Konfiguration da nicht immer hin. Die einfachste Lösung wird sein, wenn du eine extra Partition für **/boot/** erstellst, die muss mit dem **ext2**-Filesystem sein. Womöglich klappts dann automatisch. Wenn nicht, musst du dich wohl durch die man-pages von yaboot, yaboot.conf und ybin durchquälen. ;)

---

