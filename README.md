# rundeck-studies

Rundeck studies. Just for fun.

```bash
# Create docker environment
docker-compose up --build -d
docker-compose logs -f # Wait for message "Host XXX is ready" for ubuntu containers

# Configure SSH authentication between Rundeck and servers
docker-compose exec rundeck bash -c "ssh-keygen" # (Press 'Enter' for all prompts)
docker-compose exec rundeck bash -c "ssh-copy-id -o StrictHostKeyChecking=no root@linux_server_01" # (Enter 'verysecurepassword' for password prompt)
docker-compose exec rundeck bash -c "ssh-copy-id -o StrictHostKeyChecking=no root@linux_server_02" # (Enter 'verysecurepassword' for password prompt)

# Follow the executions in rundeck UI, that appends log to this file:
docker-compose exec linux_server_01 bash -c "tail -f /my_log_file.txt"
docker-compose exec linux_server_02 bash -c "tail -f /my_log_file.txt"

# Access the Rundeck UI
curl -L http://localhost:3009 # -L option follows redirects
```
