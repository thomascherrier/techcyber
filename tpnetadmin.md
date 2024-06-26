
![logo](https://visa.cefim.eu/wp-content/uploads/2023/06/LogoCEFIM-hd.png)

# PROJET NETADMIN TECHCYBER2024_1

## Préambule / Création Entreprise
![LOGO Générique](https://store-images.s-microsoft.com/image/apps.27845.30be3330-280f-4e8e-ac1d-35f4f8176e71.bee1f510-c788-4634-97f7-1edb3738e3f1.ce090a7e-7c5d-45fa-91b2-c964e56e10d9)

* Créer un groupe de 3/4 personnes (shuffle via ploufplouf, affinités).
* Créer un pool de ressources collaboratives Online type GoogleWorkspace,OneDrive/Teams, Notion
* Choisir une identité visuelle (un nom,logotype,typo,2 couleurs,un motto).
* Créer un descriptif de la société sur une feuille A4.
* Créer un organigramme de la société, vous êtes le service IT dans la DSI.
* Créer un fichier XLSX et CSV de 2000 personnes qui seront réparties dans au moins 5 services.

*Validation par le référent/formateur avant la phase suivante*

## Infra Réseau WAN

![WAN ](https://www.cloudflare.com/resources/images/slt3lc6tev37/6ARE3uWw7nvYn4VhyNh1Z6/d92a3e1bfa0878adb6c93ac91b12b98f/what_is_WAN_wide_area_network.png)

* Choisir une prise RJ45 dans la salle.
* Se coordonner avec Roger (alternant Réseau) pour s'interconnecter à la baie
* Demander à Roger/Thomas une adresse IP Publique
* Tester la prise brassée dans la salle de cours directement sur une poste
* Chercher/Monter un PC avec deux IF, 1 écran et un clavier
* Installer IPFire via une clé usb bootable
* configurer le WAN correctement sur la partie IPFire et vérifier qu'un ping sur www.perdu.com fonctionne bien
* configurer le LAN rapidement (sans DHCP) sur une adresse IPv4 privée de classe B en /22

*Validation par le référent/formateur avant la phase suivante*


## Infra Réseau LAN

![LAN](https://1.bp.blogspot.com/-4Om1fcaJZEE/YP7Rtvwxg_I/AAAAAAAADYA/fBPxXW_u44YxZTZtRxI-_nYeESBxOUbkACLcBGAsYHQ/w640-h474/LAN.jpg)

* Choisir et configurer un switch manageable dlink, le configurer et l'adresser correctement
* Choisir et configurer une borne WIFI (la mettre temporairement) en mode serveur DHCP

## Changement de WAN & de switches

* Remplacer IPFire par [PFSense](https://atxfiles.netgate.com/mirror/downloads/) sur le routeur matériel
* Remplacer le switch D-Link par 2 cisco catalyst et créer dedans une vlan database correspondant à vos services qui sera diffusée par VTP
* Mettre une adresse ip pour chaque switch type 172.16.3.2XX
* déclarer des ports dans chaque vlan

## Routage Intervlan

* créer une vlan database identique à celle des switches dans le routeur
* réflechir à une plan de subnetting
* créer les subgtw et les liens au vlans
* créer une règle de pare-feu pour laisser passer les flux
* créer un DHCP multipool dans le PFSense

## VPN

* Installer le paquet OpenVPN Client via le gestionnaire de paquet de PFSENSE
* Créer une autorité de certification dans le menu CERTIFICAT
* Créer un certificat serveur à partir de l'autorité ci-dessus
* Créer des utilisateurs dans user manager en leur attribuant un certificat client/utilisateur
* Créer un serveur VPN Client2Site dans le menu OPENVPN à partir du tuto fourni en annexe
* Rajouter une règle Passoire dans l'onglet OPENVPN des Rules du Firewall
* Rajouter une règle dans les rules de WAN pour le protocole IPV4 UDP : * en IP source, * en port source, destination : WAN Address en IP, 1194 en port destination , gateway *

## Livrables finaux et restitution 

* Rédaction des livrables en groupe
* Rédaction en MD si possible
* Avec ScreenShots
* A déposer en Individuel en ligne (git,hebergement web, MS365/Google Workspace)
