Commands to allow incomming traffic: 
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo firewall-cmd --reload

Create www-deploy user. This user will only have access to /vat/www/html
sudo adduser -s /sbin/nologin www-deploy
# Define o dono como www-deploy e o grupo como nginx
sudo chown -R www-deploy:nginx /var/www/html
# Permite que o dono escreva e o grupo leia
sudo chmod -R 755 /var/www/html

configure the variables on github Settings > Secrets and variables > Actions and create:

    SSH_PRIVATE_KEY: key to be used on www-deploy.
    REMOTE_HOST: 137.131.199.56
    REMOTE_USER: www-deploy
