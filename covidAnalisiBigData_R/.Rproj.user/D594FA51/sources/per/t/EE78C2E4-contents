rm(list=ls()) # rimuove tutto quello che avevo prima
library(Hmisc) # importazione di Hmisc

# configurare la propria cartella contenente /dataset o datasets/ con il percorso del proprio sistema operativo

data <- read.csv("~/Desktop/covidAnalisiBigData_R/COVID19_line_list_data.csv")
describe(data) # comando Hmisc 

# ripulire colonna delle morti verticale
data$death_dummy <- as.integer(data$death != 0)
# morti su base temporale importata
sum(data$death_dummy) / nrow(data)

# ANNI
# panoramica: le persone che muoiono sono più anziani
dead = subset(data, death_dummy == 1)
alive = subset(data, death_dummy == 0)
mean(dead$age, na.rm = TRUE)
mean(alive$age, na.rm = TRUE)
# questa statistica è significativa?
t.test(alive$age, dead$age, alternative="two.sided", conf.level = 0.99)
# normalmente con i dati importati, se p-value < 0.05, rigettiamo l'ipotesi di un null
# molto significante sulla base dei dati ricevuti

# GENERE
# nessun effetto sui risultati
men = subset(data, gender == "male")
women = subset(data, gender == "female")
mean(men$death_dummy, na.rm = TRUE) #8.5%
mean(women$death_dummy, na.rm = TRUE) #3.7%
# significativo o meno?
t.test(men$death_dummy, women$death_dummy, alternative="two.sided", conf.level = 0.99)

