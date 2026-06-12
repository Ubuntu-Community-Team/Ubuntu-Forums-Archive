---
title: "[SOLVED] Archivo undecript!!!"
date: 2008-04-13
forum: Argentina Team
---

### Post by wanchan on 2008-04-13
Hola, estaba tratando de firmar los codigos de conducto CoC, cuando recibi el mensaje que tenia que copiarlo en editor de texto, eso hice y luego tenia que decencriptarlo con el comando:
gpg --decrypt nombreArchivo 
Salida:
colivieri@colivieri-desktop:/home$ gpg --decrypt colivieri/OpenPGPKey.txt
gpg: No se han encontrados datos OpenPGP válidos
gpg: decrypt_message failed: eof

Nota: el archivo esta en el dirctorio colivieri, y no en /home, no creo que sea por eso que no pude decencriptarlo.

---

### Post by oktubrer on 2008-04-13
Asegurate de que en el archivo hayas copiado también el encabezado y el fin que indican que el mensaje está encriptado:

-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.2.2 (GNU/Linux)

(texto encriptado)

-----END PGP MESSAGE-----

---

### Post by wanchan on 2008-04-13
Si lo copie todo:
Hello,

This message contains the instructions for confirming registration of an
OpenPGP key for use in Launchpad.  The confirmation instructions have been
encrypted with the OpenPGP key you have attempted to register.  If you cannot
read the unencrypted instructions below, it may be because your mail reader
does not support automatic decryption of "ASCII armored" encrypted text.

Exact instructions for enabling this depends on the specific mail reader you
are using.  Please see this support page for more information:

    [https://help.launchpad.net/ReadingOpenPgpMail](https://help.launchpad.net/ReadingOpenPgpMail)

For more general information on OpenPGP and related tools such as Gnu Privacy
Guard (GPG), please see:

    [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.3 (GNU/Linux)

hQQOA3GishlrS9ySEBAAibPAGbZgZ9S+jW86fYGpTjj1CRJwq/CLeOcv6rGZhYtj
/XFWrw0pMUMTE8EhGdJhlLe1/mDPTaosKjgOGNP2b+slklNEScoIyugD6WYHa1xs
jo3l02Ud4lZXzUdHeYlkLqkpFFNsUSfoaKaNPDDrtxLh4DfZuyAEmE0GzbBbSfEp
QifE9lXn136UEwxEM/S1HpWZ5zMqRkYTND1YeUvQBujttn9mX/f8ouj34W1/9HhL
17i5I1c7vzWT7l6AQLDpFowBO4hdUpRDMrmOItOp7O+pC3qmgv9LGMb/rQ2DF9C/
xuByMAVychn58fxyTtAuo2ydHZq/Isc2t96/F1zRFCMDZZJlMHNpwh9FwoRb8yck
XF5a/wwr0Yh1VjYdvjxBq8aKok7Q2uejDRuHEWGSf/SOLoIjdsnpVf1EEuLrTtBS
8Gs3C3v+OVeseyX65Bn7wWiHUiG8A5ULgQ0CUJsPtc04KCPqkIz7WA1GfiJZeScq
Jd3+svRm07ueGc6JI+0lnb16BE36wh6Be9cqpv0XCUmq/IgMK6/p0LNCt2QzIu9j
Wyf7M1fABpp3Qhv7CQTHvPMHrmk4nbgHRuby/H9/JHUN4eHDe1RBMOvV+WBiDPqf
/FGSJScyJPGh47a1bTil4Ukby1lW1/bbrl3O0LpxQUI9L0PPHMraYKuKqPaC8KUP
/25YYDG+VN54JLQJoKzOXSoXRPae+z+Gc6sunFOIi/Zw0JBHoVdT37TaABjo14No
aQOXO5jXUisS9M7hHTu04GT/qoMEvpRNbpaZ6KbChwywDdi8HKYTrPKk/kzALdim
NS4h1OIOWeRCpmWWxQm+107A3eokYJJYN3TxDeCWnrNd6EW4HOTt46l74xkdXTTo
imJ0uybFAQoq1tuEDuVR8ijPeQ88gggiC6ASf6eOPi0tSWwBZFC6PfiDR/546bqV
m+OB4LLtef897gDm1hrfConPhSErmMYYQvZA8VaCVMmkUz9ig9mCil5juQrtpxdn
A10nlgSIRt8uSfZj6FRr8GVRN+JdhK41JjWWUMky11s7qy1od7U9rL3BAegcyM0t
3UXbbNmp0dj0F0Gejg//wAUv04AVk1eDhzjKFhzPkbnWk3u/BWcztJiwTdooFNxI
dyGU03MOZdf8+0iaIWucXq2FY5pwb68jJWwKwKEyMq9IBD5C5May4mIAzc1LM2Go
76r4wHsdJuUUwFNHi2ruVImY6QRwvPPjpYCMOWqme5ZLjtY29ALK6B1HrSVy8TrH
mcS3kL8uAvQr+aGwSPNzMycKYLyqlMYB1sAf4QNYWleZ6rbso83ph0KgSNjiv+OE
fSjNsdUndBKhq10bicwQ5g/sZmUf92J4Xj4eqSAGIh5V0sCwARQNTc65vmC8Nvrk
0T4a8RMv134tBwgKikbnGZeB6thK45PmvDER0id3UuXywF4oggL05aEeIiRp3nEH
h4AU+vX2wlW8Pj0T0cHFZWEf4OAFf9eBlRrbKIV+RRKYHJQGihvXXy703M+kfKTd
VgPUJK77yNsUOmj+b4ArNaN48bq/QSpFvm3dqBkTZJNoBBN9QbMYwzTWDNq43Rmw
ALVDbXrS2XWrcNOJGL4x1VCWeuB1tfnCC1e61gWxe4TI6TSZU+j274McQ4FrhOXL
knXpIPXppqzG5Lpx4w9+JSnEHp187uHDhcwWzGm9nRwz9TPjuXToi7LHNyW2wJBp
FhUqUfLMAiY0+HhCHJOqTL5HcNmD0MaSDdEugG7/qLJfAeg8VJXL2pV+U76ue0J2
6Ioj8v1Ju7MXlK5rJISqRvIB+UU145HGZnPPS/QhoFcyj8UoQXPZQBupjy71/nWu
vQXO7vahwtVi2TrObNU5aT+3NgA=
=kBnh
-----END PGP MESSAGE-----
Thanks,

The Launchpad Team

O tengo que copiar solo desde -----BEGIN PGP MESSAGE----- hasta -----END PGP MESSAGE----- ?

---

### Post by oktubrer on 2008-04-13
> **wanchan said:**
> O tengo que copiar solo desde -----BEGIN PGP MESSAGE----- hasta -----END PGP MESSAGE----- ?

Exacto! solo eso

---

### Post by wanchan on 2008-04-13
Hice un copy paste de esto:
-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.3 (GNU/Linux)

hQQOA3GishlrS9ySEBAAibPAGbZgZ9S+jW86fYGpTjj1CRJwq/CLeOcv6rGZhYtj
/XFWrw0pMUMTE8EhGdJhlLe1/mDPTaosKjgOGNP2b+slklNEScoIyugD6WYHa1xs
jo3l02Ud4lZXzUdHeYlkLqkpFFNsUSfoaKaNPDDrtxLh4DfZuyAEmE0GzbBbSfEp
QifE9lXn136UEwxEM/S1HpWZ5zMqRkYTND1YeUvQBujttn9mX/f8ouj34W1/9HhL
17i5I1c7vzWT7l6AQLDpFowBO4hdUpRDMrmOItOp7O+pC3qmgv9LGMb/rQ2DF9C/
xuByMAVychn58fxyTtAuo2ydHZq/Isc2t96/F1zRFCMDZZJlMHNpwh9FwoRb8yck
XF5a/wwr0Yh1VjYdvjxBq8aKok7Q2uejDRuHEWGSf/SOLoIjdsnpVf1EEuLrTtBS
8Gs3C3v+OVeseyX65Bn7wWiHUiG8A5ULgQ0CUJsPtc04KCPqkIz7WA1GfiJZeScq
Jd3+svRm07ueGc6JI+0lnb16BE36wh6Be9cqpv0XCUmq/IgMK6/p0LNCt2QzIu9j
Wyf7M1fABpp3Qhv7CQTHvPMHrmk4nbgHRuby/H9/JHUN4eHDe1RBMOvV+WBiDPqf
/FGSJScyJPGh47a1bTil4Ukby1lW1/bbrl3O0LpxQUI9L0PPHMraYKuKqPaC8KUP
/25YYDG+VN54JLQJoKzOXSoXRPae+z+Gc6sunFOIi/Zw0JBHoVdT37TaABjo14No
aQOXO5jXUisS9M7hHTu04GT/qoMEvpRNbpaZ6KbChwywDdi8HKYTrPKk/kzALdim
NS4h1OIOWeRCpmWWxQm+107A3eokYJJYN3TxDeCWnrNd6EW4HOTt46l74xkdXTTo
imJ0uybFAQoq1tuEDuVR8ijPeQ88gggiC6ASf6eOPi0tSWwBZFC6PfiDR/546bqV
m+OB4LLtef897gDm1hrfConPhSErmMYYQvZA8VaCVMmkUz9ig9mCil5juQrtpxdn
A10nlgSIRt8uSfZj6FRr8GVRN+JdhK41JjWWUMky11s7qy1od7U9rL3BAegcyM0t
3UXbbNmp0dj0F0Gejg//wAUv04AVk1eDhzjKFhzPkbnWk3u/BWcztJiwTdooFNxI
dyGU03MOZdf8+0iaIWucXq2FY5pwb68jJWwKwKEyMq9IBD5C5May4mIAzc1LM2Go
76r4wHsdJuUUwFNHi2ruVImY6QRwvPPjpYCMOWqme5ZLjtY29ALK6B1HrSVy8TrH
mcS3kL8uAvQr+aGwSPNzMycKYLyqlMYB1sAf4QNYWleZ6rbso83ph0KgSNjiv+OE
fSjNsdUndBKhq10bicwQ5g/sZmUf92J4Xj4eqSAGIh5V0sCwARQNTc65vmC8Nvrk
0T4a8RMv134tBwgKikbnGZeB6thK45PmvDER0id3UuXywF4oggL05aEeIiRp3nEH
h4AU+vX2wlW8Pj0T0cHFZWEf4OAFf9eBlRrbKIV+RRKYHJQGihvXXy703M+kfKTd
VgPUJK77yNsUOmj+b4ArNaN48bq/QSpFvm3dqBkTZJNoBBN9QbMYwzTWDNq43Rmw
ALVDbXrS2XWrcNOJGL4x1VCWeuB1tfnCC1e61gWxe4TI6TSZU+j274McQ4FrhOXL
knXpIPXppqzG5Lpx4w9+JSnEHp187uHDhcwWzGm9nRwz9TPjuXToi7LHNyW2wJBp
FhUqUfLMAiY0+HhCHJOqTL5HcNmD0MaSDdEugG7/qLJfAeg8VJXL2pV+U76ue0J2
6Ioj8v1Ju7MXlK5rJISqRvIB+UU145HGZnPPS/QhoFcyj8UoQXPZQBupjy71/nWu
vQXO7vahwtVi2TrObNU5aT+3NgA=
=kBnh
-----END PGP MESSAGE-----

En Open Office y lo guarde como OpenPGPKey.odt, pero no me lo descencripta. 
gpg: No se han encontrados datos OpenPGP válidos
gpg: decrypt_message failed: eof

---

### Post by leo_rockway on 2008-04-13
> **wanchan said:**
> Hice un copy paste
<snip>

En Open Office y lo guarde como OpenPGPKey.odt, pero no me lo descencripta. 

Usa texto plano, no openoffice.

---

### Post by sajnox on 2008-04-13
Texto Plano = Aplicaciones\Accesorios\Editor de textos

---

### Post by wanchan on 2008-04-13
Listo gracias a los que respondieron!!!, creia que no importaba la extension del archivo.

---

### Post by wanchan on 2008-04-13
Como hago para poner el post como SOLVED?

---

### Post by sajnox on 2008-04-13
En thread tools tenes la opcion para marcarlo (al inicio del thread a la izquierda)

Una ultima aclaracion, en Linux la extension del archivo es solo anecdotica, el sistema reconoce el contenido no la extension de los archivos

---

### Post by leo_rockway on 2008-04-14
> **sajnox said:**
> 
Una ultima aclaracion, en Linux la extension del archivo es solo anecdotica, el sistema reconoce el contenido no la extension de los archivos

Una forma de comprobar esto es el comando file:

```
$ file holamundo.py
holamundo.py: python script text executable
$ mv holamundo.py holamundo
$ file holamundo
holamundo: python script text executable

```

La extensión está para guiarte a vos, no a la computadora. La diferencia entre odt y txt no es la extensión sino el contenido y la forma en que se almacenan los datos.

---

