---
title: "Problema entre Ubuntu Karmic Koala, Firefox i router ONO model Amper"
date: 2009-11-01
forum: Catalan Team
---

### Post by Ivan Roig on 2009-11-01
Hola Ubuntaires!

M'he instal·lat de soca-rel el nou Xubuntu (més que res, per a formatar el disc en ext4, que he llegit que el pot fer anar una mica millor), però un cop instal·lat he tingut problemes a l'hora de navegar per internet, atès que les pàgines trigaven molts segons a carregar-se'm. 

Donada la meva imperícia en aquests temes, m'he passat tota la tarda cercant la solució per fòrums, i entre que els que trobava no em funcionaven i que cada pàgina nova de la recerca em suposava 20 segons d'espera, he estat a punt de sucumbir a la desesperació.

Afortunadament, acabo de trobar una pàgina que m'ha salvat del desfici ([aquesta]("http://my.opera.com/pascasio/blog/2009/10/17/error-grave-entre-karmik-koala-firefox-y-router-ono-modelo-amper"), en castellà), i que dóna la solució per a un problema que es produeix si uses el Firefox del Karmik Koala i tens un mòdem Amper de la companyia ONO (com és el meu cas). Per si algú també s'hi troba, són quatre passes:

(1) Obrim el Firefox i a la barra de l'adreça escrivim: **about:config**

(2) A la barra on diu "filtre" escrivim: **network.dns.disablelPv6**

(3) Fem doble clic damunt d'on diu "false", que es converteix en "true". 

(4) Tanquem el Firefox i hi tornem a entrar. Ja deuria funcionar. Vaja, a mi m'ha funcionat!

Però com que no tinc ni punyetera idea del que acabo de fer, les meves preguntes són: ¿què he fet? i ¿pot provocar-me alguna conseqüència indesitjada?

---

### Post by papapep on 2009-11-01
> ¿què he fet? 

Has inhabilitat la compatibilitat amb [IPV6]("http://ca.wikipedia.org/wiki/IPv6") que és la propera versió del protocol [IP]("http://ca.wikipedia.org/wiki/Protocol_d%27Internet") que s'està implantant.

> 
i ¿pot provocar-me alguna conseqüència indesitjada? 

No. Per ara [IPV4]("http://es.wikipedia.org/wiki/IPv4") és l'estàndard que funciona, gairebé, a tot arreu sense problemes. Queda temps per a fer servir l'IPV6.

---

### Post by quitus on 2009-11-03
T'agraeixo molt que hagis fet aquest fil explicant això, a mi també amb passava, potser no tant exagerat, només 5 segons, ara va perfecte.

salut.

---

