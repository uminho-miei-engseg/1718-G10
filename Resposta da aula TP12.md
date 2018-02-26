
1) Questões da Parte1 da Aula

Experiência 1.1 Resposta:

Foram gerados 1024 bytes pseudo aleatórios

34ZVjddAJQUv+HMqfjBPuN+f+viTqpLCeR2FnRp1S+vXewe0/Vcaf7+FVKeRMep7
k/pW8KHUrmmaEjcZY7ByJD4kIRBzBxzE2e/52MmWDDsk9bfPPAtIXRumsuqV/urw
WmfvIt2crSJQrOm8oXeTknHuk/tXz7b9PmmAPkhoojG9NxGS0dpNjG3RL0yydmCR
sKmXGeELtPM3ks3x1hUp728DV3uKUl13bDPBTdHFgukQcZtOpb9gdE+2DEA2Hhp2
skwH+yUZ3PfvcqKVagX/oF0ervpSbIDodzrUwTQd0yklMVSYrQtqrccbw6FEDZCz
A6J/8sDxKaRPOACEulpyJKT1tc2QyjVxjuZlkw8Vq45CqiRR1jtuYF+SDnQXiuSt
DZb6m1GQDrTiNthysXrNzZZuisolsuUIfKWnUK6XUerNXdHOolS9iOJ1hJ/CQpe8
HUNfyo/+fIdtLUmylkisWqUoy++Ew3o5FgPP13uBvI8YA4K7eNHdgNU6eyYBzTEO
eHjK6couuOCRU9xpwfJcXM5rbevyp+PpHzSE1hc+xuQdm7cwo/Hjsy5lVgworhE2
GtqZeqP5gsH8uRcv7UePM4Dbarn8iiVtyXkE9ShtRlLHiVaNcCbl0v+2I85/j1Ix
ecDVXBiO8Fjv0vwIxvxxh0PV1wnagSF+B6fIs6G/kTQd5cw6+gue1fqdDlejcOft
+MyJiLkzdOagKDx39GjJB1PYQsbOXwwmEUvReKYl8WpIaLA2/0xAP7pkhC1CfXGi
9FaTkbwJbIyDIvk+imqPPW9ELaqH8ABGv5PuzPBHBQWAiwlI1VtLxzBKcLxwg+ow
NJQiz3wf9fHOo6y2BZ3NcBp3v/X+rEePFxNqyot0munmIXjomz3w7jy/6vqFBawE
uvF4ETbfo0nc7ENgvqvLUv1a2SmOTcVDw3wpsJp5VZDFMQu9ndtsHjKwBGMkcvEQ
dwCld2+zdOGIKiEc9U4ijdSNqGtpMBzdvLZcDtJ5HuSkAj/FaoreCD9BBMDIO4XP
QlGp5ahCv/QWs9ycNHLx9nylgEBn8PYjkNWOOmGG8XG3Wz5qtwrslQMD/uL0FfCb
YBJwQe+DmFaecv3xkvXQS974PzF/X5J8FWcaoVoAC1GjFrwpt6tHNI/dWU73cOwc
HE0X+Oo+9hlg5ieapiysRBKtrziENZtsXgcTHIZO0Hma8RpGG0wrYgFX5Vn6i3kt
Tz2Hsdvfal+2PdDTGl8uvrVvSoXSvARze4nENoQobPTcCHePwFyBR+7YkHpmODzw
tvrANbTrFV57+c05v9nDeHm2cHaednWgavjOpEWYaIs4FOyGh9GPHcSI+s2FboCi
Q8ah84RFPsKCoZT8pISD3A==

Pergunta 1.1 Resposta:

Na execução do primeiro comando, para 1024 butes, não foi gerado nenhum byte, porque a máquina precisa de muita entropia.mas se
reduzirmos para 24 ou 40 bytes serão gerados os bytes pseudoaleatórios, visto que neste caso a máquina não precisa de entropia. No
segundo foram gerados os 1024 bytes pseudoaleatórios, pelo facto de introduzir urandom, os bytes pseudoaleatórios são gerados sem 
precisar de entropia. 
Nos baseamos nos resultados obtidos após a execução dps respectivos comandos.

Pergunta 11.2 Resposta

O primeiro comando permitiu gerar 1024 bytes pseudoaleatórios sem presisar da entropia por causa da intalação da package haveged, 
que é um gerador de bytes pseudoaleatórios. Para chegar à estas conclusões baseamo-nos nos resultados obtidos durante a execução 
dos comandos após a instalação da package haveged.

Pergunta 1.3 Resposta:

Analisamos o programa e notamos que dentro do ciclo while existe o código:

s = utils.generateRandomData(secretLength - l)
        for c in s:
            if (c in (string.ascii_letters + string.digits) and l < secretLength): # printable character
                l += 1
                secret += c

Que permitiu gerar uma string com um comprimento dado no input da função.

2) Quesões da Parte2 da Aula

Pergunta 2.1 Reposta: 

Com o comando: openssl genrsa -aes128 -out mykey.pem 1024, gerou-se um par de chaves e por sua vez, com o comando python
createSharedSecret-app.py 7 3 1 mykey.pem. Foi introduzido a mesma passphrase que na geração da chave privada, assim como o 
segredo "Cifra indecifrável". Para verificar se as 3 partes necessitam da reconstrução do segredo. Em primeiro lugar deve-se 
criar o certificado associado à chave privada com o comando: openssl req -key mykey.pem -new -x509 -days 365 -out mykey.crt 
nota-se que foi criado o ficheiro: mykey.crt, referente ao certificado. O comando:
python recoverSecretFromComponents-app.py 3 1 mykey.crt para obter o segredo a partir das componentes. 
Ap+os a introdução das 3 componentes necessárias, fez-se a recuperação do segredo.

Pergunta 2.2 Resposta:

Notabilizou-se que, o número de componentes necessários para reconstruir o segredoé que permite diferenciar os programas 
um do outro.

3) Questões da Parte3 da Aula

Pergunta 3 Resposta:

Daria as seguintes sugestões:
1- Usar a cifra simetrica salsa 20 para cifrar o segredo
2- Gerar chaves aleatóriamente com tamanhos maior 2⁸⁰ para garintir maior segurança(no nosso caso usamos 256 bits).                                                                                                                                                                        como experiência)
3- Gerar um mac da mensagem cifrada que sera enviada em conjunto, para garantir autenticidade.
4- Para decifrar, oreceptor recebe o criptograma juntamente com o mac correspondente, calcula o mac da mensagem e compara
com o recebido. Se ambos forem iguais, o segredo é autêntico e se não forem iguais implica dizer que o segredo foi vitima
de ataque. Deve-se rejeitar a mensangem recebida.

O algoritmo para resolver o referido problema é:

{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 85,
   "metadata": {},
   "outputs": [],
   "source": [
    "# decifar uma mensagem\n",
    "from Crypto.Cipher import Salsa20\n",
    "from cryptography.hazmat.backends import default_backend\n",
    "\n",
    "\n",
    "def cifra(k, txt):\n",
    "    \"\"\" Função que cifra a mensagem 'txt' usando a chave 'k'\"\"\"\n",
    "    cipher = Salsa20.new(key=k)\n",
    "    return cipher.nonce + cipher.encrypt(txt)\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 86,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "b'\\xb4\\xfe\\r\\xaaF\\xe2\\xe0jB\\xe2\\xc0\\x7f{\\x86\\x9a\\xd2\\x03nb\\xf3\\x90\\x88P'\n"
     ]
    }
   ],
   "source": [
    "# testar a função 'cifra'\n",
    "secret = b'*Thirty-two byte (256 bits) key*'\n",
    "ctxt = cifra(secret, b'Uma mensagem...')\n",
    "print(ctxt)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 87,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "b'arquivo da impresa' HASH= b'Y+\\x98\\xc4\\xc32C\\x036\\x06\\xfb\\x07V\\xcd\\xea\\x9dfj\\x87\\x85\\x07\\xf3\\x01\\xb0\\x81\\xe6\\xa9\\xef<\\x1d\\x9d\\xd6'\n"
     ]
    }
   ],
   "source": [
    "from Crypto.Cipher import Salsa20\n",
    "\n",
    "msg_nonce = msg[:8]\n",
    "ciphertext = msg[8:]\n",
    "\n",
    "\n",
    "\n",
    "\n",
    "secret = b'*Thirty-two byte (256 bits) key*'\n",
    "cipher = Salsa20.new(key=secret, nonce=msg_nonce)\n",
    "digest = hashes.Hash(hashes.SHA256(), backend=default_backend())\n",
    "plaintext = cipher.decrypt(ciphertext)\n",
    "digest.update(plaintext)\n",
    "h = digest.finalize()\n",
    "\n",
    "print(plaintext, \"HASH=\", h)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 88,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "32\n"
     ]
    }
   ],
   "source": [
    "from cryptography.hazmat.primitives import hashes\n",
    "\n",
    "digest = hashes.Hash(hashes.SHA256(), backend=default_backend())\n",
    "digest.update(b\"abc\")\n",
    "digest.update(b\"123\")\n",
    "res = digest.finalize()\n",
    "print(len(res))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 89,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "b'\\xdbP\\xa2*\\xe4q^\\xcb\\xa51}\\xa2Z\\x81]\\x86\\xcb\\xa2\\xfbP\\x95\\t6E3V,i\\xfb\\xc40f'"
      ]
     },
     "execution_count": 89,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "from cryptography.hazmat.primitives import hashes, hmac\n",
    "h = hmac.HMAC(secret, hashes.SHA256(), backend=default_backend())\n",
    "h.update(b\"message to hash\")\n",
    "h.finalize()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.6.3"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}


4-
detalhes da chave utitilizada

Base 64-encoded

CN=ZETES TSP QUALIFIED CA 001, SERIALNUMBER=001, O=ZETES SA (VATBE-0408425626), C=BE

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


Signature Algorithm: SHA256WITHRSA
            Signature: a87c4d5316d5f835e44ff202a7b61cbcdf4785b2
                       54ac538b9ad12d35f37056752f8bceeb409b3400
                       efeda96295909ac590a31a5c047a3c536c9e87e4
                       702b3664d852059ce510797aecb6ada40060f9b8
                       f3f01bf4cd51aa8013b1662a2b2790dfd1607fd9
                       d00eeda8407a524b5f3ca3be1604a8901e5050ea
                       b7c18eccc512d7a6120b6538b23bae757f1827c8
                       86ad2b1d505dc61011795f3f52c28bf726e24494
                       f56646eeb6f66f1cce28e5df86e471fcac78a0fb
                       45f8aaeef6fb048d59c86e98add43fce333cbf98
                       26fa6071f7f3a664b78dc1c504e2b06b80d73ddd
                       7c7967f010dbf5c4f427cedcad4b44f383c499a6
                       0ba7049bb89e8ac0da328680f784e95d51ac7f57
                       d195a394a166b690a74571a3faa9096855531281
                       0ed3992a2a9e56475b7dbf4ab92c9d9ded0a7169
                       b8456250e8726c72318f4568d2bd5a84adeccb2f
                       cf21a1894b7c1bb9e607b833d5df208f78563e9a
                       d7fc8e1d8a5009aa82a6a9b486c43aaf98af3b5d
                       e9ae46aa19602c96a867a5f7b92ec3e645a08bbd
                       ed7073a4e65db8ff04a7a2d6935b8211a9940366
                       62f9181cf5bef8042ae0e182e60efd6c0845c56b
                       7c37e9107a925a3c13623f78b35a851e2e453a58
                       86c2b2b84b6c64e3f5fb4d916682db5fb1e6641c
                       2b6ef03c24ca74499924b37ce14bf0c8ca60228a
                       83c43dc43da8cc9bc24a968db6e2d181e64837e2
                       b478d6c1d5d8ecdb280d6a3b


Algoritmo usado:


SEQUENCE {
   SEQUENCE {
      [0] {
         INTEGER 0x02 (2 decimal)
      }
      INTEGER 0x3820ee9c74ecd147
      SEQUENCE {
         OBJECTIDENTIFIER 1.2.840.113549.1.1.11 (sha256WithRSAEncryption)
         NULL 
      }
      SEQUENCE {
         SET {
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.4.6 (countryName)
               PrintableString 'BE'
            }
         }
         SET {
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.4.10 (organizationName)
               UTF8String 'ZETES SA (VATBE-0408425626)'
            }
         }
         SET {
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.4.5 (serialNumber)
               PrintableString '001'
            }
         }
         SET {
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.4.3 (commonName)
               UTF8String 'ZETES TSP ROOT CA 001'
            }
         }
      }
      SEQUENCE {
         UTCTime '160520172029Z'
         UTCTime '260520172029Z'
      }
      SEQUENCE {
         SET {
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.4.6 (countryName)
               PrintableString 'BE'
            }
         }
         SET {
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.4.10 (organizationName)
               UTF8String 'ZETES SA (VATBE-0408425626)'
            }
         }
         SET {
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.4.5 (serialNumber)
               PrintableString '001'
            }
         }
         SET {
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.4.3 (commonName)
               UTF8String 'ZETES TSP QUALIFIED CA 001'
            }
         }
      }
      SEQUENCE {
         SEQUENCE {
            OBJECTIDENTIFIER 1.2.840.113549.1.1.1 (rsaEncryption)
            NULL 
         }
         BITSTRING 0x3082020a0282020100c3478f13ef9bb64d6e628baa0e00a51a6ac87a4ccca7c9057c3b195ab0fb230402a4cb39609bfe2e21a42c73a11b453c450632f6b5b1cb7c04a4c828e2e3d588135273f80cd238c2241ab79ee2dc99750921aa8f9847137e4f1f5b02464c1676dbf1c010329d046978da23738a202babcebffc6c879409e8808660ff53090a31057f45f28d74b1f684df1fc432835a2882d234d16806f4a66ce08938a6073210aaccaaf0fc1061cd5a1c0cc86746797e2c048e5c2716a2da7aa9fb7f702e4cc9fd2e15e5924d35c183033be3422391cf9cf1ffedbeffd334c0f21b371b54a67fbb04cedacf7b5f41660e2040cfdff848f29c01abe0b9335d88f4fd95910a9c910ff7dd1392bf57342388194942b189333b22bc4ba3d6ef262f2cffd03d56d1a6ab16c4b98b3859db84121417fa1853068a50d04af38bda654cca6fe7c2237cc09cf835282e7682baf91beb07549ca55f6d9b0ae2b4c0a082f42b689d4c47fd3c03f7f45f54125b0bb407831d1e5e46c5b0ed155aae8a7c0ebc7d70c39a5ea2b2bd427201d60b0478b652b82f28a15569feecea5ad16eaafa3cc9cfe1f9e23c6c67ae7c55978094770b4d847ee876533a517e799738a43e2971f6318562b9624eae52620421834228571e5189f64fa4287a805d4ee0327208603a5e54e7398a0a3d683f8a1ed6a9f858e749c5bf06abd1eb00e5152a1df1781a016ba9c0bad75f0203010001 : 0 unused bit(s)
      }
      [3] {
         SEQUENCE {
            SEQUENCE {
               OBJECTIDENTIFIER 1.3.6.1.5.5.7.1.1
               OCTETSTRING 3063303a06082b06010505073002862e687474703a2f2f6372742e7473702e7a657465732e636f6d2f5a45544553545350524f4f5443413030312e637274302506082b060105050730018619687474703a2f2f6f6373702e7473702e7a657465732e636f6d
            }
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.29.14 (subjectKeyIdentifier)
               OCTETSTRING 0414e2b4db5f6a0f025054d51defd27672722195462b
            }
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.29.19 (basicConstraints)
               BOOLEAN TRUE
               OCTETSTRING 30060101ff020100
            }
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.29.35 (authorityKeyIdentifier)
               OCTETSTRING 3016801438bc5c3054dce2bb20efee6f41a0316e5cfd8b75
            }
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.29.32 (certificatePolicies)
               OCTETSTRING 307430720604551d2000306a302c06082b06010505070201162068747470733a2f2f7265706f7369746f72792e7473702e7a657465732e636f6d303a06082b06010505070202302e0c2c5a45544553205453502043505320666f72204e43502b20616e64205143502b20636572746966696361746573
            }
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.29.31 (cRLDistributionPoints)
               OCTETSTRING 30363034a032a030862e687474703a2f2f63726c2e7473702e7a657465732e636f6d2f5a45544553545350524f4f5443413030312e63726c
            }
            SEQUENCE {
               OBJECTIDENTIFIER 2.5.29.15 (keyUsage)
               BOOLEAN TRUE
               OCTETSTRING 03020106
            }
         }
      }
   }
   SEQUENCE {
      OBJECTIDENTIFIER 1.2.840.113549.1.1.11 (sha256WithRSAEncryption)
      NULL 
   }
   BITSTRING 0xa87c4d5316d5f835e44ff202a7b61cbcdf4785b254ac538b9ad12d35f37056752f8bceeb409b3400efeda96295909ac590a31a5c047a3c536c9e87e4702b3664d852059ce510797aecb6ada40060f9b8f3f01bf4cd51aa8013b1662a2b2790dfd1607fd9d00eeda8407a524b5f3ca3be1604a8901e5050eab7c18eccc512d7a6120b6538b23bae757f1827c886ad2b1d505dc61011795f3f52c28bf726e24494f56646eeb6f66f1cce28e5df86e471fcac78a0fb45f8aaeef6fb048d59c86e98add43fce333cbf9826fa6071f7f3a664b78dc1c504e2b06b80d73ddd7c7967f010dbf5c4f427cedcad4b44f383c499a60ba7049bb89e8ac0da328680f784e95d51ac7f57d195a394a166b690a74571a3faa90968555312810ed3992a2a9e56475b7dbf4ab92c9d9ded0a7169b8456250e8726c72318f4568d2bd5a84adeccb2fcf21a1894b7c1bb9e607b833d5df208f78563e9ad7fc8e1d8a5009aa82a6a9b486c43aaf98af3b5de9ae46aa19602c96a867a5f7b92ec3e645a08bbded7073a4e65db8ff04a7a2d6935b8211a994036662f9181cf5bef8042ae0e182e60efd6c0845c56b7c37e9107a925a3c13623f78b35a851e2e453a5886c2b2b84b6c64e3f5fb4d916682db5fb1e6641c2b6ef03c24ca74499924b37ce14bf0c8ca60228a83c43dc43da8cc9bc24a968db6e2d181e64837e2b478d6c1d5d8ecdb280d6a3b : 0 unused bit(s)
}

Este certificado esta na validade e apresenta tamanho da chave e algoritmo de acordo com as recomendações dos NIST. pelo que é adequado, isto é: 
Algoritmo de assinatura: SHA256whithRSAEncryption.
Algoritmo de chaves publica: RSA Encryption.
