# Analyse
Ziel der Analyse ist die Information, welche Entitäten an ihren jeweiligen Standorten über eine ungenügende Netzabdeckung verfügen. 

# Hintergrund
## Daten Bundesnetzagentur
Die Bundesnetzagentur stellt mehrere geographische Gitter von Deutschland zur Verfügung (https://www.breitband-monitor.de/mobilfunkmonitoring).
Für die angeforderte Analyse wurde das Gitter "DE_Grid_ETRS89-UTM32_100m" genutzt, das Deutschland in 100m große Polygone unterteilt. 
Jedes dieser Polygone beinhaltet eine Information zur Verfügbarkeit der folgenden Technologien: GSM_OUT, UTMS, LTE, NR_DSS und NR.
Die Verfügbarkeit kann mit einer Zahl 0 ("unversorgt") oder 1-3 (versorgt durch 1-3 Netzbetreiber) angegeben sein. 

Beispielhaftes Polygon:
- ID: 100mN55777E3164, GSM_OUT: 3, UMTS: 0, LTE: 2, NR_DSS: 0, NR: 0

Das oben benannte Beispiel-Polygon ist anhand von 5 Koordinatenpunkten definiert:
- ID: 100mN55777E3164, KOORDINATEN: [(399799.9999999689, 5265399.99999948), (399799.9999999689, 5265399.99999948), (399799.9999999689, 5265399.99999948), 
(399799.9999999689, 5265399.99999948), (399799.9999999689, 5265399.99999948)]

Die Koordinaten sind im national etablierten UTM-Zone32-Format gemäß EPSG:25832 angegeben. 

### Erklärungen der Technologien
- "GSM, UMTS and LTE are digital cellular technologies that enable mobile network coverage. GSM stands for Global System for Mobile Communications and it is a second-generation (2G) technology that introduced SMS (Short Message Service) and mobile data on our phones through GPRS (General Packet Radio Service). UMTS stands for Universal Mobile Telecommunication System, and it is a third-generation (3G) network technology that introduced us to High-Speed Packet Access (HSPA). Finally, LTE stands for Long Term Evolution, and it is a fourth-generation (4G) network technology that can offer super-fast mobile data rates." (https://commsbrief.com/difference-between-gsm-umts-lte/)
- Gemäß der Datei "202110_Auswertung_Bund_Zusammenfassung.pdf" scheinen NR_DSS und NR für 5G_DSS und 5G zu stehen.  

## Daten Entitäten
Die Entitäten sind quer über Deutschland verteilt. Jede Entität bestand aus einer ID sowie einem Längen- und Breitengrad. 

Beispielhafte Entität (fiktiv):
- ID: 123456789, LONGITUDE: 11,34498, LATITUDE: 50,12345 

Die Koordinaten der Entitäten sind im WGS-1984-Format gemäß EPSG:4326 angegeben.

# Herangehensweise
Zur Bewertung der Netzqualität soll für den Längen-Breitengrad einer Entität das Polygon aus dem Datensatz der Bundesnetzagentur extrahiert werden, in das die Agentur hineinfällt. 
Sofern eine Agentur zufällig am Rande zwischen Polygonen liegt, wird zufällig eines der zutreffenden Polygone ausgewählt.

# Einordnung der Ergebnisse
Daten zur Breitbandmessung lagen nicht vor. Aus dem Jahresbericht der Bundesnetzagentur: "Das generelle Leistungsniveau lag bei mobilen Breitbandanschlüssen
auch im aktuellen Berichtszeitraum deutlich unter dem von stationären Breitbandanschlüssen." (S. 8)
Eine Approximation der Breitbanddaten mithilfe der Mobilfunkdaten ist mithilfe eines Abgleichs 
der von der Bundesnetzagentur zur Verfügung gestellten Landkarten möglich:
- Die Ergebnisse der Breitbandmessung der Bundesnetzagentur: https://www.breitband-monitor.de/breitbandmessung/karte
- Eine Deutschlandkarte bez. der Verfügbarkeit von 2G, 3G, 4G und 5G: "202110_MonitoringMobilfunk.pdf"
- Eine Auflistung der Mobilfunkverfügbarkeit nach Bundesländern: "202110_Auswertung_Bund_Zusammenfassung.pdf"
- Eine Auflistung der Mobilfunkverfügbarkeit nach Landkreisen: "202110_Auswertung_Landkreise_Kreisfreie_Staedte.pdf"
