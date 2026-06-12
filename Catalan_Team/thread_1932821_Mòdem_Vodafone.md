---
title: "Mòdem Vodafone"
date: 2012-02-28
forum: Catalan Team
---

### Post by rosa d'abril on 2012-02-28
Hola,
M'he baixat l'última versió de l'Ubuntu (11.10) i tinc un problema amb el mòdem USB Huawei K3765 de la Vodafone. Quan l'hi endollo, al cap de força segons, me'l reconeix i me'n demana el PIN. L'hi dono i al despleglable de les connexions de xarxa m'apareix l'opció Vodafone (HSPA). Hi clico i se'm connecta però llavors em van apareixent notificacions del tipus *You are registered now at GSM homenet* o alguna cosa així i se'm desconnecta al cap de molt pocs minuts. M'hi torno a connectar i així tota l'estona: anar connectant i desconnectant. Algú sap que puc fer per tal que la connexió sigui més estable  o pot adreçar-me a algun post anterior?
Moltes gràcies

---

### Post by wgarcia on 2012-02-28
Convindria verificar si l'Ubuntu està reconeixent el mòdem correctament. Per fer això un cop reiniciar l'ordinador i a l'escriptori, obre una terminal. Endolla el mòdem i espera uns segons que surti la notificació que l'ha vist. A la terminal entra "dmesg" i enganxa les últimes 10 línies de la parrafada que ha sortir, aquí s'hauria de veure si l'Ubuntu està veient el mòdem correctament.

---

### Post by rosa d'abril on 2012-02-28
Gràcies per la resposta.
Les deu últimes files de les moltes que em surten són aquestes:
  	 	 	 	 	 	    143.050972] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint 
 [  143.051214] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint 
 [  143.051863] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint 
 [  145.048178] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint 
 [  146.049475] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint 
 [  147.046579] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint 
 [  149.043868] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint 
 [  151.041725] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint 
 [  153.038980] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint 
 [  155.047342] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint 
   
  
Et diu alguna cosa?

---

### Post by wgarcia on 2012-02-29
Sembla un problema de la connexió USB, potser relacionat amb el mòdem USB però no estic segur. Em sembla que a vegades hi ha algun problema amb el PIN i genera aquest tipus d'errors.

Alguns suggeriments, a provar si et sembla. Amb el mòdem desconnectat: 

Mira si hi ha algun problema amb el PIN al Gestor de conexions de xarxa (Network manager). Clica sobre la icona de xarxa al plafó superior, i escull "Edita", i aquí busca les "Connexions de banda ampla" i aquí dins el teu mòdem. Esborra-li el PIN. 

Connecta el mòdem i mira si et torna a demanar el PIN. 

Una altra possibilitat és esborrar l'entrada del mòdem en aquesta aplicació i deixar que l'Ubuntu te'l torni a configurar. 

Una tercera és configurar el mòdem perquè no tingui PIN, si això no et representa un problema de seguretat (si el mòdem es de pre-pagament, si el perds tampoc és tan important que tingui PIN).

---

### Post by rosa d'abril on 2012-02-29
Hola,
He fet això que em deies: "
Clica sobre la icona de xarxa al plafó superior, i  escull "Edita", i aquí busca les "Connexions de banda ampla" i aquí dins  el teu mòdem. Esborra-li el PIN. 
[SIZE=1]Pero no ha calgut esborrar-li el PIN perquè ja estava en blanc
Després he connectat el mòdem, m'ha tornat a demanar el PIN i ara t'escric això. A veure quant aguanta. Què et sembla, provo el segon suggeriment?[/SIZE]
[SIZE=1]Gràcies novament[/SIZE]

---

### Post by wgarcia on 2012-03-02
Doncs potser una altra combinació interessant de provar és que SÍ que tingui entrat el PIN al Gestor de connexions de xarxa, a veure si és això el que fa que es desconnecti sols.

---

### Post by rosa d'abril on 2012-03-02
La primera solució que em vas donar no va funcionar. La connexió continuava tallant-se contínuament. Provaré a introduir-li el PIN d'entrada, tal com em suggereixes.
Per altra banda, ahir vaig provar la segona solució. Vaig esborrar tot rastre de la connexió de la Vodafone al Netmanager i li vaig endollar el mòdem. Em va demanar el PIN em va fer configurar la connexió una altra vegada (tres o quatre passes bastant pesadetes) i se'm va connectar SENSE NI UNA SOLA INTERRUPCIÓ fins que me'n vaig anar a clapar. Problema? Que hauria de repetir tot el procés esborrar/reconfiguar cada vegada que volgués fer servir el mòdem, cosa bastant emprenyadora.
Sigui com sigui, moltes gràcies
PD: By the way, estic bastant fins els nassos de les finestretes sobre fons negre que se'm van obrint constantment anunciant-me "You are now registered at the home net bla, bla, bla". Hi ha manera de desactivar-les?

---

### Post by wgarcia on 2012-03-02
Em sembla que no et tornarà a demanar la configuració del mòdem, la recorda un cop  que la has feta. 

En quant a les finestretes, tens bona connexió? Vull dir, amb intensitat suficient? Perquè em sembla que ho fa perquè va perdent i guanyant la connexió.

---

### Post by rosa d'abril on 2012-03-03
Sí, el problema és que recorda la configuració i llavors torna a tallar-se'm cada dos per tres. Només em funciona a la perfecció si esborro i reconfiguro la connexió cada vegada.  
Quant a les finestretes, deu ser això que dius però fins ara, és a dir, fins que m'he instal·lat l'11.10, no m'havia passat.
Salut!

---

