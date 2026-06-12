---
title: "terminal no funciona"
date: 2021-02-17
forum: Catalan Team
---

### Post by josep-maria on 2021-02-17
He actualitzat l'ubuntu mate del 20.04 al 20.10, i ara el terminal no funciona. Vegeu aquesta imatge:

[https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-15-19-38-03.png](https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-15-19-38-03.png)

Què puc fer-hi? He mirat al fòrum i no he trobat cap anomalia semblant.

---

### Post by T6&amp;sfpER35% on 2021-02-17
l'enllaç a la vostra imatge no funciona.
per què actualitzar a la 20.10 de totes maneres? és millor adherir-se a LTS

---

### Post by josep-maria on 2021-02-18
A mi em funciona. Vegem ara:

[https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-15-19-38-03.png](https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-15-19-38-03.png)

Si tecleges per exemple sudo, no veus res a la pantalla. 
L'ubuntu mate 20.04 no té els models nous d'impressores, i el 20.10, sí.

[https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-15-19-38-03.png]("https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-15-19-38-03.png")

---

### Post by wgarcia on 2021-02-18
El fòrum no mostra l'enllaç directament, suposo que per protegir-se de possibles spam. Potser pots explicar l'error que veus, o sent una terminal, copiar i enganxar el text on es veu l'error. Si és molt llarg, el pots enganxar a: paste.ubuntu.com, i enganxar l'enllaç que suposo que sí que et deixarà enganxar.

---

### Post by josep-maria on 2021-02-18
[https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-18-08-30-13.png](https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-18-08-30-13.png)

No res. He ficat l'enllaç a paste.ubuntu.com, i surt això:

Ubuntu Pastebin
Paste from josep-maria at Thu, 18 Feb 2021 15:54:41 +0000
Download as text
1
[https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-18-08-30-13.png](https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-18-08-30-13.png)
Download as text

Coi! Ara he copiat la pantalla del terminal i quan ho he enganxat aquí he vist que hi ha unes lletres que no es poden veure. Són aquestes:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

```
josep@josep-HP-Compaq-8200-Elite-SFF-PC:~$ sudo
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-T timeout] [-u user] file ...
josep@josep-HP-Compaq-8200-Elite-SFF-PC:~$ ^C
josep@josep-HP-Compaq-8200-Elite-SFF-PC:~$ hhp
```

Però jo veig això: 

josep@josep-HP-Compaq-8200-Elite-SFF-PC:


josep@josep-HP-Compaq-8200-Elite-SFF-PC:


josep@josep-HP-Compaq-8200-Elite-SFF-PC:

---

### Post by T6&amp;sfpER35% on 2021-02-18
ok al vostre primer missatge dieu que el terminal no funciona, però, tanmateix, publiqueu aquí una sortida del terminal on acabeu d'escriure "sudo".
sudo per si sol no fa res, ha d'anar seguit d'alguns arguments, per exemple "sudo reboot", que reiniciarà el PC.
no estic segur d'entendre el que vols?

---

### Post by wgarcia on 2021-02-19
A paste.ubuntu.com et mostra un enllaç un cop enganxes el text que vols mostrar, i el que has de fer és enganxar aquest enllaç perquè el puguem veure allà mateix.

Quant al que mostres, coincideixo amb el @3nd, tot es veu normal. Quin és l'error que penses que tens?

---

### Post by josep-maria on 2021-02-19
La pantalla és gairebé tota negra, jo només veig això:

------------------------------------------------------------------------------------
josep@josep-HP-Compaq-8200-Elite-SFF-PC:~$



josep@josep-HP-Compaq-8200-Elite-SFF-PC:~$



josep@josep-HP-Compaq-8200-Elite-SFF-PC:~$




-------------------------------------------------------------------------------

(aquests guinets representen els marges de la pantalla)

---

### Post by josep-maria on 2021-02-19
He ficat l'enllaç al paste ([https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-18-08-30-13.png](https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-18-08-30-13.png))
I ara què haig de fer?

---

### Post by josep-maria on 2021-02-19
Tot això de sudo, usage, etc. que us he escrit abans, no es veu. Apareix al text que escric ara quan copies la pantalla del terminal fent ctrlC i ctrlV.

---

### Post by josep-maria on 2021-02-19
El paste em diu això:

Ubuntu Pastebin
Paste from josep-maria at Fri, 19 Feb 2021 08:16:58 +0000
Download as text
1
[https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-18-08-30-13.png](https://blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-18-08-30-13.png)
Download as text

---

### Post by josep-maria on 2021-02-19
Vegem si fent-ho amb dos trossos va bé:

[https://blocs.tinet.cat/tokra/files/2021/02/](https://blocs.tinet.cat/tokra/files/2021/02/)           Captura-de-pantalla-a-2021-02-18-08-30-13.png

Cal treure els espais en blanc d'entremig.

---

### Post by josep-maria on 2021-02-19
Vegem si ara va bé:

https://
blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-18-08-30-13.png

---

### Post by wgarcia on 2021-02-19
I quin és l'error que veus exactament? El que mostra la captura és simplement la consola habitual. Si entres una ordre produeix algun error?

---

### Post by josep-maria on 2021-02-19
Que la consola està en blanc. No es veu ni l'ordre que jo hi fico ni la resposta. Si copio tota la imatge fent ctrlC i l'enganxo aquí fent ctrlV, llavors apareix la resposta, tal com us he adjuntat més amunt, al post num. 5. 
Digueu-me una ordre senzilla, la ficaré al terminal, i us mostraré què veig.

---

### Post by T6&amp;sfpER35% on 2021-02-19
```
rm -rfv ~/.cache/thumbnails
```

---

### Post by josep-maria on 2021-02-19
La finestra està tota negra, i no es veu res. Si avanço pàgines, al final torno a veure:
josep@josep-HP-Compaq-8200-Elite-SFF-PC:

Si copio tota la finestra fent ctlA ctlC, i ho enganxo aquí fent ctrlV, surt això:

4518.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/a96f9fa2dd4f2fd602ca3b531bb4f2c8.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/38c2a5f900f7868ca0a0ceef600ba177.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/cffcc405a90cd139d5afdaf106da27ca.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/1b841c9df2c7edef7b45a5a9ed586411.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/81fc00c235bb7a9bb8a09544e8bd4b7e.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/081a255b2018aea861166e675a42fc1b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/7c3b49294547b4cd466c97f614ae5bcd.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/740eccf67be82546b324550e7a86cba3.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/4f95ba1f7ee3385dc5d9b95750571c81.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/1466ba82f8e1a4fdff9d98b36df0d422.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/e85a23755542331ca9f2f45ccba8f86b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/b34c2fd5f03ffa296ff5d6dedddd9355.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/a0236207cddb76257700ea706bf4c293.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/78bc110dd52da3d12fec74837edcd402.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/f26c5b22a9c7200e302e6ed1bd54f364.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/133589043e49538d9d5f93200f9d1e79.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/19b3601c5debc36a1fa11417df3be314.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/797611a662af89226b82315abc777c52.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/5caa067eca91b2fa52bbcf90f57e572a.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/11e8409715f4c7ec67c013de12220e30.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/37fc18cfbeb288bf67998459d881d1c3.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/a8474d5ae74b459eb6f38577bbfcca07.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/a6a0507ca25286173a34e0f7102d4012.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/c4d4c459cc45172d6be90f3db2cf890e.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/412b59ffd01456bdd1b4f3599df46f58.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/26db39d4d1b13de58d758533d33eb8f5.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/fb9d052049d7850090f1f133f59fe8d5.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/d8167262f46e8d428bf394e945cab3d4.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/9d68fe91789a2f038406512527815fce.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/988666382b0255ac3401a85127514c24.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/f661bc01c8694fd98232a08dd4b47b61.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/9ca56be59fd01a90ae67cb6d459eed38.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/3a8b052fc303748fa99200c628e088ec.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/b26b0b269ea7e58818971d51d6cc4766.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/054d21a26679c0b74709a20900099897.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/29b8776c9a3aed4c5a031fdcbdff4822.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/1a01b7bbfad636963604cbdb3ae46979.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/d95174afd407b06763ab0a4477087d69.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/484b3badf74794c15b77a85299f5e17f.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/525989e03c0c3bb746bd0a478bb84644.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/538eb243340b99703d2bbfa19a463da2.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/77e15dc063df73aaba79a5c1a1ee5982.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/f42cbebe163bc87f3b424334cef3de8c.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/7d0d94c9dcdcc55ba811547111ff3b3a.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/ef95cf29527bcbe43d5ddc489224935f.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/dbc624367e74420416b03b2d078a5fcc.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/edf4f2a6c93ecf9d4e8b5f79bd7c0aa9.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/555f69de70bcded6b55e9d3dd7240eb3.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/90d82f4ef3d59099ea712399821ead0b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/8ee4b6e157c3e72648286c869b1e3ef2.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/d43aae1787dfa910c016659939f1e11b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/97139b3ba619971594dbf2376f4216f9.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/5a5c3053a775aeb55790424fcbfba53b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/b4f306605c2c22e2b31b075010ef8c14.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/fd322733da14dfa61a8776d9eb948ef2.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/d8fc437949f8ea81b606a4c5b53db91c.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/7f157535e5b1783111009f74c68c817f.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/e91159739c34080ad1dc141dc03ed635.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/cbec4f508f56acb5fd6ab59e039d2e43.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/8663d6b2debccebec8eae2eb99b9b79d.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/4f3d2d121c557fe7fdcd61e3f8b3b1f4.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/78ad72d6725be4cc55bb28fbc1f39123.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/579b8ad68862142da01c58807f29e027.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/820c9f0520abf1025a9890a22aeba7fb.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/106f103e7f24fd538fbdc3ccb23b30e2.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/d0e26f2f16919ed727d2d421dac5c8c9.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/1744a7b4d5496061a9d55bfab39d9d20.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/d5e74a65df653afeb5312ae32bb8a684.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/2cfbca607ffdd73efa70ced278036c87.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/e59a8b3f7d983d557c5365997a6bd3be.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/93ad3311c566e7ec3b87a2da74531d48.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/8b64042196f92f14330e326c5ee1e58d.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/69450260fcd77370f0606e387ad5b8b7.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/6216c95250fb6dc3bbedcf45757631c6.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/e892c40d755c3455a5a318db8b576839.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/d92fc08244f5e0116ce994c423163472.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/9b5c70513a38c10553dbb9d8b7c65d2f.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/2bea62894ba54aa0001e17acacb7661a.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/438a120c0f7669fa5eabb573e463e6e2.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/eff4927bc3223bb5c27f83566cc987a5.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/dfd4b262ef556bffc4b09c8196ec9c6d.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/39f51b68919b6f17db991da172b12a2e.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/be3d0dd059b58bf87c5102dd1af07b34.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/78d02f188425f0faa32fad42dc1a9385.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/640b392038f2c52d8195eeb22b213036.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/9fd19beb78e3d56d6ac2f800478295a2.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/82f6182a81f94bc8699148fd0e22f7db.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/a6496fdee9ea7da335052782df676243.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/c69a2a026d95094d72f991e015363433.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/82714c73fadd6d46251ba50a068da613.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/a0d0c302455218228e20bc4c36810f49.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/04c520ca9a2e5d955e8d5af03e497a54.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/5f69b67c1baf2faec7363ee961f7d535.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/217c368af3a1ee617ab75f8aafdc4672.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/0a00ea38c6ea8159d3d4554589ac818a.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/73adb24efaa4899ee2de896a10da47e0.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/b182f37fc2f5dff2861e57a13dab1a82.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/81d4431fa62bf67872a3a53b1be814f0.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/39703b10a2fd8224a5183bf22989cb4f.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/b508a7f55f4bec330b87724cf6194fc5.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/54ad09df8849497726f46d8d82acd008.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/53c1bf7f2003b4951f5c5b6ee203e2e6.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/e0f8092c7a3f5ab2df2c8b5f43560f47.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/2a88ff8e6c8bbcfe7041ac59ce8370a0.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/2e66663a10db79e310db70658bd69a32.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/c77476cd3bcb26403f8944ca1ac38a9a.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/f8fa3bfafa464413ef6e3424455718f1.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/26a05c09c27fbbd2dcb63107ea28cf4e.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/83838b2f2063bc7eac2a5dc4cc58deca.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/ea422c7b1750fe7bf5ba85bdef2b4e53.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/552358065661d92057f024eea521ea9c.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/1fcf3086b43e60fa475efbf04c63f636.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/ef1738113227861b4b0fad34ed5ebecf.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/003098d39c6506cae4a34e6136224fc5.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/383a87939ee3db211dbd6038935b9893.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/2c3c1015947d759939f44d6987949e39.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/bb0a067c71b942e9860f32b282c8a2e7.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/07b858a4046c7bced2e65130787dd33c.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/13176f685b5da77dabfb6e01187ae1d7.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/75577be70018a6675a57232cb62359c1.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/724b3fba7be0c484185e0749d9a577f3.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/eb6d4cb98a3a7c112062424f0a371f23.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/bfc0f83082fd9961bde11dbefc17df3c.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/9e329ec48ea048811d3354570bed7a2b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/0ae1161b1114818e73b501318cc932d7.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/820b076b47e8773d40cecdcb90fddc6d.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/57702ace9922bc3a564da5c298e8aeaf.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/bb5b7f1b92bef1d5d6db1e364b70caad.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/3d4f7214a47985519e89b36b093f7f6f.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/e2a6c4a3167782438433d619cd1d9c75.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/47546bc32f6c0f8b3189613082ac7701.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/6697d1c48e0971d15c3c04e8dcfa10ef.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/f0f20342e08774be8c3b8d86324a5112.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/7805c5fabe54056a1043ea5daf2e1e8a.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/5b525d811f052f0e2b64c5d0b17037bd.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/072d2d8976632c4550f8bbdd5d4e8489.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/6b844a25975ebd9bc2dd4016ab0166ae.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/946148d67942923e49125a6a35b7f2fa.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/eef8bb484a5dbba103388969addf0cf8.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/fb600b88220a5d3f012c6be2d1644b6d.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/75b59da5d1612b6ee5f1ae8505e9ad41.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/d232aae07f0fbd2cd185e00f0ca19284.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/34db237df1c83deb24fff879a3ec1a25.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/28e86718892cae23e58f35490c680569.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/1b5088fce0c962b2017622bec4d26bce.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/d94f2fd08d427b97edf856fadc6fd116.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/435881105762adf9077e870e32348680.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/e8b827dabccd872ecdc334cbd0a67d15.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/37a3861927c5d84b1da44aeeceaf65e1.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/45e70700f87aa430db22ace3441fa5d6.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/3159b47fc196bf86f60a65aefd185f74.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/c3b29f7485be763147cdf7ca3b2fcb0e.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/93a519a7ffc2c34d14bd7485c5bc74e1.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/44f7d7fc07ff351e88cffe678698f565.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/fd5852c9ed978756e4b4ae0640a497fb.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/51a95a1dce289c60fa4bf1b2758ccbeb.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/ca56c289ddda4fd40c1b05d84141f373.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/9884fa9c2379931909b44ad9b989b631.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/5c0c3e382b6420eb4e64f8233369b1c6.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/a670dabfb1107cd78ad0d48e6326236e.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/8fa44e1adc21f7647b98feb33428d46f.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/8252a272dc0ae47f28aa14e9c7c92cea.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/49b8c55a8f5c2356a3edea1a50b06eba.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/b0c1866212ca505ee1f94e51628b2739.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/f3477d930d0088ab672d71ea8aecbad4.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/c07f5ea660c0f101af5f740570618c7a.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/5218e4ce22aa977a92f2a605471941fb.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/cc3f048719fc3d857b80b03b594b4797.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/0a656da89aba9f3f95ca16c433411ebe.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/62ee79ec6beee2bb2b0d2c17cbd01fbf.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/4428691e09b0b36ae738a9d398e167d2.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/c229288710d4f2659780b24cb2f658a2.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/75597ebcc17b4c6d821d28ddf7a3688b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/d044592eabcb3b793341069eb561cf3c.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/501011ad58da29dc38ef2ea7dc35e466.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/7e0e44471e3fa278b9977db4ce7d54de.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/a53a5e2425883d465413f4f8823d352b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/067a15151eefb4f51c048a1f1ae378e5.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/8fc5a6e42df71a18a1a0bea30f5d1363.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/79ade9aeaff47c76e066920b79f77658.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/9ee82b778e6f316a2b55db10018347f1.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/953c109cc57eb40a619294de7d68617d.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/7f6a7e5f0fecf06665c5b183f6f091a2.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/182c7a36d0e2ae105660252d75493c84.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/7c26f7881c3b2a1e432a045adceb08a9.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/320e29c9c545dba26ac1f89a540b24d9.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/59b64981067ca179a7b985e901c07fc2.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/44b298a90dee0bca95967c0e7479204e.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/c8b2aab5e342acbe9989ab2421474e06.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/5ddae354b38a882f7a85c95b0892dd50.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/997ebb72d0ae8a6ca812c64abbc33285.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/f2e8031ccbced1dc63e01241a96a9a0b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/9c6f52c29155566a4197d9246f9cceec.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/2e5dcd0206a50e593908bc5b6d07b9f8.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/9ac9ed66dd74bc64349d996f8939d660.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/368c17742dc624b5c1ba3df289fa45c4.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/2d38b2ca5cc4423daae73cd17fb4e85b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/cfc49569a5e5ba5c1f31dcca5a6332f0.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/0348d0484b68b970b7da0278c353b32e.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/915dbd1d131456c7da4b3186e4900606.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/cee98944c7a392eaf67e627de6f9f5e8.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/067e0f3d0027c7a709fc39902f182309.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/b42b55adf779a58fb7a278226db6f72b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/09a4da2d4d86385eb1aa0df01826a4c9.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/67da6deae6e9c63cc46d9ccf7f328d53.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/629eb42fcb6e57f1dc8eb44faa6936e2.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/ccad4f64aa8c3a38519ad9e4981d28db.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/48bdd8b2291c5726d9b96d694d7ed7c0.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/232452739897f38374a90812b2da0e8c.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/decbaec751b32d2b07cd3460a10e9bf5.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/9db43f9fe9aca946f5e14f75adfe4fed.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/ca43f35ea3047adeb6ad5008c5037cd3.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/afa2a527d2f8e8b421ac41a8f739dda8.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/2403df072520500ffff3dc12c15938de.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/bea373979c097953fa88545e00ba4d22.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/56bfb216af64098986e7934c2ab86db1.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/65fb0fe70b4e1a45b227baf2ee34a6d4.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/5256007befe7aa8a82311eb660d0882c.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/718c2b13c1291e47df8ed19084b8944a.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/81889f2d7ae24b9eca58d8ed5acc737a.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/89f9201bce6e6e8e0556c72ccc11a2a2.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/3dc2323238a4ce53aaf973dfd7815f4f.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/bd75790078339b10941e64fbb6601e06.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/76ea543fe5d3949ea74ef188abfdd0e5.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/01491c84bf4514baabbace1934825746.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/a8be6a0c005a5046a9387670037f9658.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/c0b7cf4eb29804d3fdc0781e5e19d7b1.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/850bd1f31ecf3bdf4c23e50fd0702430.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/0d906f87eb671fce430a10ecd1d74b32.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/6a9e02fa72f46419ddc92904ffcd999b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/4cc2cacb4c73f9eed289d0b151482168.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/02b3d7a0848a8fb1b6637191b2dd8fe3.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/82dca6d35a40cd33fddec90312b15953.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/4f9f96df6cbbd8984ab0c5debf2eca90.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/2c278258281bfe22fd4e56a7088bd0d5.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/5637571a69989344a493d31b790184a0.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/5c879d14f9a1e2cd1da4ea21c90780f0.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/d1974214ea55c6faf97fc5d6317dd01d.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/7d582cce89cf0ac103a6a3b97bf003e4.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/19f6de853e659ad17e716708cd5f6cfd.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/5b6dd3b11674349aa77639c57014c6e6.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/7105026004afba3f7264d94b247dfb4b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/2d9f12919af6a554c43d1844793ea4d8.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/26ff1f2079fafb5ee2d3fa51c3240068.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/8781342f6e6ebaffd457329c55117c1b.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/cb2e44f83833a458e3c9b1e461058123.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/45b51adc3ea00aa1a26c4c27addaaab0.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/565cf8a2c86e37fe31f03abcc4d40bd3.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/84792a893dbc3f51349531d13a627acb.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/ec104d5cb2ed42f812b51a4da5405f78.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/4802669f7b2c7a89c469dc7e8b318b50.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/58f45cc14013d41813a96cfcf52ddfc1.png'
s&#8217;ha eliminat '/home/josep/.cache/thumbnails/normal/c16b7795e26e03e66ac9cd0f18d5e652.png'
s&#8217;ha eliminat el directori '/home/josep/.cache/thumbnails/normal'
s&#8217;ha eliminat el directori '/home/josep/.cache/thumbnails'
josep@josep-HP-Compaq-8200-Elite-SFF-PC:~$

---

### Post by wgarcia on 2021-02-20
Compte amb :

```
rm -frv
```

pots fer destrosses, les opcions "-fr" li diuen que esborri tot sense preguntar. 

És normal que a la terminal no hi hagi res, si no dones cap ordre. Què et surt si entres per exemple:

```
uname -a
```

que normalment t'hauria de mostrar quin nucli de Linux tens?

---

### Post by josep-maria on 2021-02-20
Sempre veig la pantalla negra, fiqui l'ordre que fiqui, tal com us he mostrat abans:

https://
blocs.tinet.cat/tokra/files/2021/02/Captura-de-pantalla-a-2021-02-18-08-30-13.png

---

### Post by wgarcia on 2021-02-21
No conec la terminal que es fa servir a MATE (mate-terminal?), però potser és un problema de configuració de la terminal. Pots provar primer amb alguna altra terminal a veure si pot ser això, per exemple amb xterm, no sé si ve per defecte a Mate, o instal·lar "terminator" que és la meva terminal favorita. Si aquestes terminals funcionen bé es pot mirar a la configuració de mate-terminal a veure si canviant el color de la lletra o tocant alguna altra configuració, s'arregla.

---

### Post by josep-maria on 2021-02-23
Ja ho he trobat! Cal anar a edita > preferències del perfil > colors. Moltes gràcies.

---

