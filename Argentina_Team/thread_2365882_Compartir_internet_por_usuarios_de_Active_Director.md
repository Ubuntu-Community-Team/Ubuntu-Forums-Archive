---
title: "Compartir internet por usuarios de Active Directory con squid"
date: 2017-07-11
forum: Argentina Team
---

### Post by hernancaio on 2017-07-11
Buenas gente, les comento lo que me pasa, estoy aprendiendo sobre Ubuntu Server (16.04) antes habia aprendido muchas cosas en Debian y ahora por motivos de mi trabajo me pidieron que implemente algunas cosas en Ubuntu Server, vi que es bastante parecido, en fin, hace un par de años cuando se me dio por aprender a usar Debian recuerdo q habia encontrado una forma de compartir internet a usuarios de windows simplemente validando su sesion, recuerdo que llegue a ver el AD (Active Directory) en el Debian, todo con squid, intente hacerlo en el Ubuntu y hace como 4 dias que no puedo, lo unico que consegui fue poder validar mi usuario con la sentencia [COLOR=#000000][FONT=courier]/usr/local/bin/squid_ldap_auth -R -b "dc=example,dc=local" -D [EMAIL="squid@example.local"]squid@example.local[/EMAIL] -W /etc/squid3/ldappass.txt -f sAMAccountName=%s -h dc1.example.local[/FONT][/COLOR]
ahora la pregunta del millon, **se puede hacer lo que pretendo?**, es decir que un usuario inicie su sesion en una pc (el proxy lo puedo configurar a gusto si es transparente o no y lo hago por gpo) y de a cuerdo al usuario le asigne el acceso a internet o no, una vez q consiga eso empezaria a ver el tema de los diferentes niveles de acceso, lo primero que trato de hacer es eso, que por ejemplo, el jefe de personal vaya a cualquier pc, inicie su sesion y tenga internet, mientras que los usuarios comunes no, estoy casi seguro q si se podia con la version vieja del squid y en debian, solo que no le encuentro la vuelta en el Ubuntu, cualquier hilo que me den me iluminaria algo, intente buscar info en todo lado y la mayoria que encuentro es de pfsense y CentOS y como no estoy muy familiarizado con esos comandos como que me pierdo un poco, creo que la vez anterior instale apache y samba pero no recuerdo para q y no encontre la pag q habia visto esa vez.... el entorno que manejo es el siguiente un Windows Server 2012R2 como DC el proxy que seria mi Ubuntu Server y maquinas clientes con windows que van desde el XP hasta el 10, mil gracias por cualquier ayuda, un saludo.

---

